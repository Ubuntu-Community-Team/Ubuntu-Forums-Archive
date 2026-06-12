---
title: "Configuring LDAP"
date: 2006-02-22
forum: Networking &amp; Wireless
---

### Post by greymoose58 on 2006-02-22
I'm attempting to set up user authentication on a server running Breezy as a terminal only installation. The plan is to be able to use Dan's Guardian to restrict the sites our kids can visit without permission while not impacting our own surfing. I'm also looking at using the authentication for a mail server. After a bit of looking around I settled on LDAP as the best option. 

I've got it installed but I can't get the configuration correct. When I try to do an ldapsearch it tells me:

# search result
search: 2
result: 34 Invalid DN syntax
text: invalid DN

I've gone back over all of the tutorials and such I can find and I can't find what I have done wrong. I've posted my slapd.conf below. If anyone can point me in the direction of my mistake I'd appreciate it greatly.  

# This is the main slapd configuration file. See slapd.conf(6) for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Schema check allows for forcing entries to
# match schemas for their objectClasses's
schemacheck     on

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd.args

# Read slapd.conf(5) for possible values
loglevel        0

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
checkpoint 512 30

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend                <other>

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=murphyrobertson,dc=com"




# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attrs=userPassword
       by dn="cn=admin,dc=murphyrobertson, dc=com" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=murphyrobertson, dc=com" write
        by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=murphyrobertson, dc=com" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be bdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix         "dc=debian,dc=org"

---

### Post by juicemansam on 2006-06-29
Just to answer to an old post of which I encountered a similar problem to. The error posted is the same error I obtained when trying to delete an entry. I was using the -f switch and a file that contained a just added entry. Upon looking at the ldapdelete documentation the example only had "cn=delete me,dc=example,dc=net", but my file's first line was "dn: cn=delete me,dc=example,dc=net". The "dn: " was causing the syntax error (I don't know about the rest of the file entries because I deleted them and left only the first line). I believe the solution to the syntax error is similar.

---

