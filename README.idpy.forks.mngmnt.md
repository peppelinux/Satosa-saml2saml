# PySAML2

````
git clone -b pplnx-v5 https://github.com/peppelinux/pysaml2
cd pysaml2/

# create current idpy master
git checkout --orphan idpy-v6.5.1
git remote add idpy https://github.com/IdentityPython/pysaml2.git
git reset --hard
git pull idpy master

# create current pplnx branch to be updated and tested
git checkout --orphan pplnx-v6.5.1
git reset --hard
git pull idpy master

# pplnx's patches
# https://github.com/IdentityPython/pysaml2/pull/602/files
# SPID requirements
git pull origin date_xsd_type

# https://github.com/IdentityPython/pysaml2/pull/628
# SPID required
git pull origin disabled_weak_algs

# https://github.com/IdentityPython/pysaml2/pull/778
git pull origin shibsp_enc

# https://github.com/IdentityPython/pysaml2/pull/782
git pull origin destination

# https://github.com/IdentityPython/pysaml2/pull/783
git pull origin issue_instant

# https://github.com/IdentityPython/pysaml2/pull/625
# this must be merged at the end, otherwise break the unit tests
git pull origin ns_prefixes
````

# SATOSA

````
git clone https://github.com/peppelinux/satosa
cd SATOSA
git remote add idpy https://github.com/IdentityPython/SATOSA.git
git checkout --orphan idpy-v7.0.1
git reset --hard
git pull idpy master

pip install -r tests/test_requirements.txt

# install mongodb first!
apt install -y gnupg wget
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/4.4 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
apt update
apt install -y mongodb-org
systemctl start mongod

# check that tests are ok
py.test tests/ -x

# pplnx's patches
# https://github.com/IdentityPython/SATOSA/pull/220
git pull origin DecideBackendByTarget

# https://github.com/IdentityPython/SATOSA/pull/324
git pull origin context_state_error_msg

# https://github.com/IdentityPython/SATOSA/pull/325
git pull origin error_redirect_page

# https://github.com/IdentityPython/SATOSA/pull/365
git pull origin context_http_headers

# https://github.com/IdentityPython/SATOSA/pull/366
git pull origin idphint_ms

````
