---
title: "openVPN frustration"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by NetSkay on 2009-03-19
hello
i had similar problem when setting up openSSL with apache, but i lost hte print outs somewhere so im stuck and going crazy again trying to setup openSSL but this time for openVPN... well im really trying to setup openVPN

my problem comes from when i try to execute the vars file from directory /etc/openvpn/easy-rsa/2.0
here is the vars file:
```

# easy-rsa parameter settings

# NOTE: If you installed from an RPM,
# don't edit this file in place in
# /usr/share/openvpn/easy-rsa --
# instead, you should copy the whole
# easy-rsa directory to another location
# (such as /etc/openvpn) so that your
# edits will not be wiped out by a future
# OpenVPN package upgrade.

# This variable should point to
# the top level of the easy-rsa
# tree.
export EASY_RSA="`pwd`"

#
# This variable should point to
# the requested executables
#
export OPENSSL="openssl"
export PKCS11TOOL="pkcs11-tool"
export GREP="grep"


# This variable should point to
# the openssl.cnf file included
# with easy-rsa.
export KEY_CONFIG=`$EASY_RSA/openssl.cnf $EASY_RSA`

# Edit this variable to point to
# your soon-to-be-created key
# directory.
#
# WARNING: clean-all will do
# a rm -rf on this directory
# so make sure you define
# it correctly!
export KEY_DIR="$EASY_RSA/keys"

# Issue rm -rf warning
echo NOTE: If you run ./clean-all, I will be doing a rm -rf on $KEY_DIR

# PKCS11 fixes
export PKCS11_MODULE_PATH="dummy"
export PKCS11_PIN="dummy"

# Increase this to 2048 if you
# are paranoid.  This will slow
# down TLS negotiation performance
# as well as the one-time DH parms
# generation process.
export KEY_SIZE=1024

# In how many days should the root CA key expire?
export CA_EXPIRE=3650

# In how many days should certificates expire?
export KEY_EXPIRE=3650

# These are the default values for fields
# which will be placed in the certificate.
# Don't leave any of these fields blank.
export KEY_COUNTRY="US"
export KEY_PROVINCE="VA"
export KEY_CITY="Norfolk"
export KEY_ORG="Cube Studios"
export KEY_EMAIL="netskay@gmail.com"

```

and when i run it i get input like this but with all the various "commands" or w/e from openssl.cnf file included

```

netskay@lnx-openVPN:/etc/openvpn/easy-rsa/2.0$ . ./vars
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 10: HOME: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 11: RANDFILE: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 12: openssl_conf: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 17: oid_section: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 18: engines: command not found
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 37: default_ca: command not found
dir: cannot access =: No such file or directory
dir: cannot access \:\:KEY_DIR: No such file or directory
/etc/openvpn/easy-rsa/2.0/openssl.cnf: line 43: certs: command not found

```

etc.

so im sorry for cursing but WTF do i do, i tried sudo and whatnot...
im using the original openssl.cnf that came with easy-rsa/2.0

(cries)

---

### Post by NetSkay on 2009-03-19
i was doing it wrong, i just changed the last variables, ie. country, province, email, etc. however when i do

. ./vars and then i do sudo ./clean-all i get

Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.


then i type in sudo ./build-ca and i get

  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.


whats up with that?
btw, i deleted the old config i was doing and started fresh with this

---

### Post by uzi09 on 2009-03-19
Hey,

if you're interested (or anyone else that drops by the the thread), I made a screencast of myself setting up a basic OpenVPN install from start to ping :)

[http://www.youtube.com/watch?v=BfZV4MnGfkk](http://www.youtube.com/watch?v=BfZV4MnGfkk)

---

### Post by uzi09 on 2009-03-19
> **NetSkay said:**
> i was doing it wrong, i just changed the last variables, ie. country, province, email, etc. however when i do

. ./vars and then i do sudo ./clean-all i get

Please source the vars script first (i.e. "source ./vars")
Make sure you have edited it to reflect your configuration.


then i type in sudo ./build-ca and i get

  Please edit the vars script to reflect your configuration,
  then source it with "source ./vars".
  Next, to start with a fresh PKI configuration and to delete any
  previous certificates and keys, run "./clean-all".
  Finally, you can run this tool (pkitool) to build certificates/keys.


whats up with that?
btw, i deleted the old config i was doing and started fresh with this

two things:

1. sudo gives errors with OpenVPN. Just become root:
```
sudo su
```

2. try ```
source vars
``` instead of ```
../vars
```

---

