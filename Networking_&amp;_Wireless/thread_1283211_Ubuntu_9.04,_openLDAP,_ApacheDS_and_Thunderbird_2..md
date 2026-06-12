---
title: "Ubuntu 9.04, openLDAP, ApacheDS and Thunderbird 2."
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by sdaau on 2009-10-05
Hi all, 

Well, I'm pretty happy the way Thunderbird's profile system and address book work (easy to backup, once you know where your profile folder is), but after collecting addresses on several PCs, I have addresses all over the place, and I have a difficult time collecting them all together. So I thought about trying a central home LDAP server as a single, central address book. 

Unfortunately, Thunderbird 2 only has possibilities to read a LDAP address book, but not edit one [5][6], however Thunderbird 3 seems to aim toward LDAP writing/editing [41] - and without editing capabilities, it will still be difficult to maintain a central address book, even with a LDAP server :) Unfortunately, there don't seem to be plugins for LDAP editing for Thunderbird 2 either [13] (*While [AddTo Miru Directory Server](https://addons.mozilla.org/en-US/thunderbird/addon/3345) may seem interesting, it doesn't work with LDAP directly*).

Since I had some trouble setting the whole thing to work (*plenty of references as can be seen - wish Ubuntu forums allowed anchor link to manage those*), I thought I'd document the process for Thunderbird 2 using a LDAP server on Ubuntu 9.04 (Ubuntu 9.04 was used for both desktop and server here). The server version is: 
```

$ slapd -VV
@(#) $OpenLDAP: slapd 2.4.15 (Mar 19 2009 10:08:25)

```

Also, since I have difficulties understanding LDAP schemas and such, I thought I'd use a GUI tool [14][17] to make sure everything goes well on the server side - tried several (gq, ldaptool/LDAPExplorerTool [15]), however I think I prefer Apache Directory Studio a.k.a. ApacheDS [22-24][27]. 

One of the biggest difficulties is that OpenLDAP apparently has changed its configuration ways recently, and so there are tutorials referring to both old and new setups - but, as noted in [19]:
[quote=http://ubuntuforums.org/showthread.php?t=980713]
8.10 uses the new openldap configuration([http://www.ubuntu.com/getubuntu/rele...n=config%27%27](http://www.ubuntu.com/getubuntu/releasenotes/810overview#OpenLDAP%20using%20%27%27cn=config%27%27))
openldap is moving to storing its configuration in and ldap backend. It will no longer use the single file slapd.conf.
[/quote]
For example, [1] refers to a newer setup. 

While that may explain the missing **/etc/ldap/slapd.conf** on Ubuntu 9.04 - the problem is that, in order to get this to work, you need to import the mozilla schemas into openLDAP - and to do that, you *still* need a slapd.conf file, which then gets converted to the new configuration format using **slaptest** (havent found a method yet to explain importing mozilla, or other schemas, directly into the new type of openLDAP configuration directory). Thankfully, a sample /etc/ldap/slapd.conf can be found in [2]. 

Then, there are in fact, two Mozilla schemas that were meant for Thunderbird: **mozillaAbPersonAlpha.schema** can be found in [3], and **mozillaOrgPerson.schema** can be found in [42]; in this example, mozillaAbPersonAlpha is being used. The schema browser functionality of ApacheDS (and other GUI tools) can be used to control whether this schema has been imported succesfully when the openLDAP server was configured. This part of the process has been collected in a script called **convldap.sh**, given below.
[i][list]
[*] Note that the schema importing process here in convldap.sh is sort of broken, and asks for reconfiguration of slapd package, which should be done according to script instructions.
[*] Note that convldap.sh mixes some old and new approaches, such as trying to reset the ldap password - this is probably not needed.
[*] Note that convldap.sh uses ldapadd (instead of slapadd) to add the converted schemas.
[/list][/i]

Once the LDAP server has been configured and running, and shows the mozillaAbPersonAlpha schema, one can continue with exporting the local address book from Thunderbird 2 in LDIF format. Unfortunately, this exported LDIF address book file cannot be directly imported into the LDAP server using ApacheDS - fortunately, there is the **abookconvert.php** script from [11], which can be used to generate a converted LDIF file - which can then be imported in the openLDAP server using ApacheDS. 


--------------------------------------------------------

So here is a basic sequence of commands that would be performed on the server: 
```

# make sure openLDAP is installed
sudo apt-get install slapd ldap-utils
# possibly reconfigure to set server address, password etc 
sudo dpkg-reconfigure slapd

# make a working directory
mkdir ~/ldapsetup
cd ~/ldapsetup

# get a convldap.sh file in this ~/ldapsetup directory
# get a slapd.conf.orig file in this ~/ldapsetup directory
# get a mozillaabpersonalpha.schema in this ~/ldapsetup directory
# get a init.ldif in this ~/ldapsetup directory
# get a template2.ldif in this ~/ldapsetup directory

# this command will ask for LDAP password multiple times, and will dpkg-reconfigure slapd
./convldap.sh

```

This example assumes that you have set up a DNS to point to your server at **myserver.somehosteddomain.com** (edit the files correspondingly), and that you have opened port 389 on your router (see [4] - note this example does not deal with SSL) - else you won't be able to connect to your LDAP server. It also assumes the openLDAP user is 'admin'. 


You can here test at the client, if there is a connection to the LDAP server using ApacheDS, by making a "new LDAP connection":
[list]
[*] in Bind DN or user do not just enter "admin" or "openldap", use the full string "cn=admin,dc=myserver,dc=somehosteddomain,dc=com" which is shown by "ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb" !! Then auth is succesful. (as per [22])
[*] Next screen - Fetch Base DNs, and click "Finish".... 
[*] Now, in ApacheAD click Workbench, and then you see LDAP Browser as in [23]
[/list]
and check if the mozilla schema is there (Rightclick in the connection in Connections, and Open Schema Browser - not the "perspective" schema browser). 


Then, you can export an Thunderbird address book as per [11] (Tools / Address Book - Tools / Export, LDIF), and obtain a, say, myaddbook.ldif file - which will be converted:
```

sudo apt-get install php5-cli # if you need it 

# remember to edit the abookconvert.php file first!
php abookconvert.php <myaddbook.ldif >myaddbook-out.ldif

```

Then you should be able to import the converted myaddbook-out.ldif file into the LDAP server using ApacheDS (on the client). If you set ApacheDS not to stop on errors during import, then you don't have to worry about duplicate entries either (*it seems the ApacheDS import procedure is not case sensitive for the duplicates, while the php conversion script itself is. problematic/duplicate entries will be logged in a *.ldif.log file*)


Finally, to set up Thunderbird to use your LDAP server, follow [11]: in Thunderbird's "Edit / Preferences / Composition / Adressing / Edit directories":
[list]
[*] Base DN - enter the address book you want to access  ou=personal,dc=myserver,dc=somehosteddomain,dc=com
[*] Bind DN - enter your login entry cn=admin,dc=myserver,dc=somehosteddomain,dc=com
[/list]


--------------------------------------------------------

The script **convldap.sh** is: 

```

# uncomment to debug command output
# set -x

# get current dir
THISFILE=$(readlink -f $0)
THISDIR=$(dirname $THISFILE)
echo Script: $THISFILE, dir: $THISDIR

echo "Enter LDAP password (you'll need to type it again when slapd reconfigures, though) and press [ENTER]:"
stty -echo
read LDAPPASS
stty echo

# copy conf file (can dissapear if sed below goes wrong) and schema
cp -f $THISDIR/slapd.conf.orig slapd.conf
# sudo cp -f $THISDIR/mozillaorgperson.schema /etc/ldap/schema
sudo cp -f $THISDIR/mozillaabpersonalpha.schema /etc/ldap/schema

# stop server
sudo /etc/init.d/slapd stop

# clean/reconstruct ldap dir
sudo rm -rf /etc/ldap/slapd.d
sudo mkdir /etc/ldap/slapd.d

# lets set new password and try capture hash here
# check old contents
echo $(cat $THISDIR/slapd.conf | grep SSHA)

PWDRESP=`slappasswd -s $LDAPPASS`
# escape slashes in PWDRESP
PWDRE=$(echo "$PWDRESP" | sed 's/\//\\\//g')
echo $PWDRE

# try change the current hash into slapd.conf
# the commented line below compacts everything in a single line !
# echo $(cat $THISDIR/slapd.conf | sed -e "s/{SSHA}.*/$PWDRE/g") > $THISDIR/slapd.conf
sed -i "s/{SSHA}.*/$PWDRE/g" $THISDIR/slapd.conf

# check
echo $(cat $THISDIR/slapd.conf | grep SSHA)

# we gonna get slaptest: bad configuration directory!
# if we are not in /etc/ldap/
sudo cp -f $THISDIR/slapd.conf /etc/ldap

# convert old-style slapd.conf to new style dir
sudo slaptest -f /etc/ldap/slapd.conf -F /etc/ldap/slapd.d

# change owner of new style dir
sudo chown -R openldap:openldap /etc/ldap/slapd.d

## test restart server
#sudo /etc/init.d/slapd restart

# stop server again
sudo /etc/init.d/slapd stop

# allow /var/lib/ldap to be erased, and erase it
sudo chmod -R 766 /var/lib/ldap
sudo rm -rf /var/lib/ldap/*

# set orig perms back to /var/lib/ldap
sudo chmod 750 /var/lib/ldap


# add init and template
sudo slapadd -v -l $THISDIR/init.ldif
sudo slapadd -v -l $THISDIR/template2.ldif


# change owner (as it gets to be root now)
sudo chown -R openldap:openldap /var/lib/ldap

# restart server again
sudo /etc/init.d/slapd restart

# check if server there
ps axf | grep slapd

cat <<EOF

Well, due to problems with password, here we rerun the entire config.
Please answer NO to all questions (listed below) and note that 
the process will fail. 
However, do enter EXACTLY the SAME PASSWORD you entered at 
start of this script, when asked in the wizard (doublecheck the
other settings as well). 

Omit OpenLDAP server configuration? NO
Do you want the database to be removed when slapd is purged? NO
Move old database? NO
Allow LDAPv2 protocol? NO
EOF

read -p "Then press Enter when ready..." 
sudo dpkg-reconfigure slapd

# at this point, the server is probably dead so restart once again
sudo /etc/init.d/slapd restart

# check if server there
ps axf | grep slapd

# test connection - this doesn't ask for password
ldapsearch -x

# must do these to have the classes show in LDAP GUI tools
# passed password, so it is not asked each time
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{0\}core.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{1\}collective.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{2\}corba.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{3\}cosine.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{4\}duaconf.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{5\}dyngroup.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{6\}inetorgperson.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{7\}java.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{8\}misc.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{9\}nis.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{10\}openldap.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{11\}ppolicy.ldif
ldapadd -x -H ldap://myserver.somehosteddomain.com/ -D "cn=admin,cn=config" -w $LDAPPASS -f $THISDIR/schema_ldif_conv/cn=\{12\}mozillaabpersonalpha.ldif


echo "Here enter the same LDAP password (already entered thrice)...."
# test connection - password will be asked, must work for remote
ldapsearch -xLLL -b cn=config -D cn=admin,cn=config -W olcDatabase={1}hdb


```


--------------------------------------------------------

Note that for Thunderbird:
[list]
[*] If you've set up the LDAP directory to be your default address book in Thunderbird 2, note that you won't get any addresses in your address book, until you type '.' in the search field (unlike for local address books) 
[*] However, if you're offline, and you've cached (downloaded) the LDAP address book for offline use (Thunderbird Preferences / Composition / Adressing / Directory server - Edit Directories / Edit / Offline / "Download Now"), then all entries in the address book cache are displayed (like for local address books) 
[*] If you have abook.mab in your profile directory as your local address book, the cache for the LDAP server will be a file in the same directory called, say, abook-1.mab
[/list]

Few more notes: 
[list]
[*] Typical errors I'd get: during connection "** The authentication failed: LDAP: error code 34 - invalid DN", during schema import "Superior attribute type 'name' does not exist", "Syntax with OID 1.3.6.1.4.1.1466.115.121.1.25 does not exist", "Inconsistent duplicate attributeType: 'mozillaCustom1'", "LDAP: error code 50 - no write access to parent" ... Not sure if all of them are gone :) 
[*] the last # makes a problem in .schema files ("line 10: unknown directive <#> outside backend info and database definitions.")
[*] If there are problems with ApacheDS, deleting its directory ```
rm -rf /home/username/.ApacheDirectoryStudio
``` and restarting it may help
[*] If starting to run into Invalid Credentials with openLDAP - 'sudo dpkg-reconfigure slapd' again may help fix it (when also purging the slapd database)
[*] If "Starting OpenLDAP: slapd" freezes at boot... try reconfigure from safe mode - drop to root shell prompt and 'dpkg-reconfigure slapd'. If again it wont start, then 'apt-get purge slapd' and then reinstall - it should help. 
[*] To debug slapd, add '-d5' to $SLAPD_OPTIONS in /etc/init.d/slapd 
[/list]


--------------------------------------------------------

**References:**
[LIST=1]
[*] [OpenLDAP Server](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)
[*] [Installing And Configuring OpenLDAP On Ubuntu Intrepid Ibex | HowtoForge - Linux Howtos and Tutorials](http://www.howtoforge.com/installing-and-configuring-openldap-on-ubuntu-intrepid-ibex)
[*] [MailNews:Mozilla LDAP Address Book Schema - MozillaWiki](https://wiki.mozilla.org/MailNews:Mozilla_LDAP_Address_Book_Schema)
[*] [HowTo: Create LDAP server for shared Address Book in Thunderbird - Ubuntu Forums October 5th, 2006](http://ubuntuforums.org/showthread.php?p=1582401)
[*] [Sharing address books - MozillaZine Knowledge Base](http://kb.mozillazine.org/Sharing_address_books#LDAP)
[*] [Bug 86405 - Make LDAP addressbooks editable](https://bugzilla.mozilla.org/show_bug.cgi?id=86405)
[*] [LDAP addressbook](http://cweiske.de/tagebuch/LDAP%20addressbook.htm)
[*] [Lightweight Directory Access Protocol - Wikipedia, the free encyclopedia](http://en.wikipedia.org/wiki/Lightweight_Directory_Access_Protocol)
[*] [OpenLDAPServer - Community Ubuntu Documentation](https://help.ubuntu.com/community/OpenLDAPServer)
[*] [Thunderbird:Help Documentation:Connecting to an LDAP address book - MozillaWiki](https://wiki.mozilla.org/Thunderbird:Help_Documentation:Connecting_to_an_LDAP_address_book)
[*] [Sharing an Address Book via an LDAP Server using Mozilla Thunderbird Versions 1.0 and 1.5](http://www.sudleyplace.com/LDAP/index.en.html)
[*] [Sharing address books - MozillaZine Knowledge Base](http://kb.mozillazine.org/Sharing_address_books)
[*] [Search Add-ons (ldap) :: Add-ons for Thunderbird](https://addons.mozilla.org/en-US/thunderbird/search?q=ldap&cat=all)
[*] [LDAP management GUI - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=317227)
[*] [LDAP Explorer Tool: a multi platform LDAP browser and editor](http://ldaptool.sourceforge.net/)
[*] [OpenLDAP and GUI tools](http://www2.kuh.kumamoto-u.ac.jp/jsato/ldapmemo/ldapsetup.htm)
[*] [Dedicated OpenLDAP GUI? - The Suretec Blog](http://blog.suretecsystems.com/archives/25-Dedicated-OpenLDAP-GUI.html)
[*] [Apache Directory Studio - Features](http://directory.apache.org/studio/features.html)
[*] [(ubuntu) Where is the slapd.conf in Intrepid? - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=980713)
[*] [OpenLDAP Software 2.4 Administrator's Guide: Configuring slapd](http://www.openldap.org/doc/admin24/slapdconf2.html)
[*] [LDAP Troubleshooting](http://kb2.adobe.com/cps/195/tn_19576.html)
[*] [Apache Directory Studio LDAP Browser - User's Guide - Getting Started - Create connection](http://directory.apache.org/studio/static/users_guide/ldap_browser/gettingstarted_create_connection.html)
[*] [Apache Directory Studio LDAP Browser - User's Guide - Getting Started - Browse the directory](http://directory.apache.org/studio/static/users_guide/ldap_browser/gettingstarted_browse.html)
[*] [Apache Directory Studio LDAP Browser - Schema Editor User's Guide](http://directory.apache.org/studio/static/users_guide/schema_editor/)
[*] [Apache Directory Server v1.5 - Add your first elements to the schema](http://cwiki.apache.org/DIRxSRVx11/add-your-first-elements-to-the-schema.html)
[*] [OID description for 1.3.6.1.4.1.13769.2.2.1 - mozillaOrgPerson](http://www.alvestrand.no/objectid/1.3.6.1.4.1.13769.2.2.1.html)
[*] [ Apache LDAP Studio&#12391;LDAP&#12399;&#12418;&#12358;&#24598;&#12367;&#12394;&#12356; Google Translate: LDAP is more afraid of the Apache LDAP Studio ](http://translate.google.dk/translate?hl=en&sl=ja&u=http://www.atmarkit.co.jp/fjava/rensai3/eclipseplgn21/eclipseplgn21_3.html&ei=CA3BSpqsHI3W-QabrL23AQ&sa=X&oi=translate&resnum=10&ct=result&prev=/search%3Fq%3D%2522Apache%2BDirectory%2BStudio%2522%2B%2522new%2Bschema%2Bproject%2522%26hl%3Den%26safe%3Doff%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DG)
[*] [LDAP Attributes. Properties Active Directory Users Computers Distinguished name](http://www.computerperformance.co.uk/Logon/LDAP_attributes_active_directory.htm)
[*] [OpenLDAP 2.4 - Notes (itsecureadmin.com)](http://itsecureadmin.com/wiki/index.php/OpenLDAP_2.4)
[*] [LDAP V3 schema (publib.boulder.ibm.com)](http://publib.boulder.ibm.com/infocenter/tivihelp/v2r1/topic/com.ibm.IBMDS.doc/progref11.htm)
[*] [Re: How to backup/restore on remote servers](http://www.openldap.org/lists/openldap-technical/200906/msg00202.html)
[*] [(SOLVED) ldap can't connect - Zimbra - Forums](http://www.zimbra.com/forums/installation/18270-solved-ldap-can-t-connect.html)
[*] [Re: slapd giving me startup errors.](http://www.openldap.org/lists/openldap-software/200508/msg00044.html)
[*] [RE: Re: Re: ldapadd -> ldap_bind: Invalid credentials](http://www.openldap.org/lists/openldap-software/200206/msg00165.html)
[*] [Re: why '{SSHA}***' method is "Invalid credentials (49)"?](http://www.mail-archive.com/openldap-software@openldap.org/msg08461.html)
[*] [Additional info: objectclass: value #1 invalid per syntax - Dev Shed](http://forums.devshed.com/ldap-programming-76/additional-info-objectclass-value-1-invalid-per-syntax-595090.html)
[*] [Ldap Person example using OpenLDAP [Archive] - Spring Community Forums](http://forum.springsource.org/archive/index.php/t-33744.html)
[*] [Re: Apache Directory Studio and Sun DS: msg#00018 users-directory-apache](http://osdir.com/ml/users-directory-apache/2009-02/msg00018.html)
[*] [Re: Apache Directory Studio schema editor - getting started](http://mail-archives.apache.org/mod_mbox/directory-users/200806.mbox/%3c98d8c0860806040934r6ca382ag7ab9ff645a8577a4@mail.gmail.com%3e)
[*] [LDAP is NOT a Database! - O'Reilly Sysadmin](http://www.oreillynet.com/sysadmin/blog/2006/05/ldap_is_not_a_database.html)
[*] [Nabble - Mozilla - Directory - Write to ldap addressbook - Thunderbird 3.01 Alpha](http://www.nabble.com/Write-to-ldap-addressbook---Thunderbird-3.01-Alpha-td14344264.html)
[*] [mozillaOrgPerson schema - Bugzilla](http://bugzilla.mozilla.org/attachment.cgi?id=104858&action=view)
[/LIST]

---

### Post by sdaau on 2009-10-05
For completeness: 

here is a **slapd.conf.orig** - *basically the same as slapd.conf in [2], with added include for mozillaabpersonalpha.schema, and server setup (replace with values for your server before using - and make sure you do the same with all the scripts referring to a server name)*

```

# This is the main slapd configuration file. See slapd.conf for more
# info on the configuration options.

#######################################################################
# Global Directives:

# Features to permit
# allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema
# include         /etc/ldap/schema/mozillaorgperson.schema
include         /etc/ldap/schema/mozillaabpersonalpha.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args

# Read slapd.conf(5) for possible values
loglevel        none

# Where the dynamically loaded modules are stored
modulepath    /usr/lib/ldap
moduleload    back_hdb

# The maximum number of entries that is returned for a search operation
sizelimit 500

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.
tool-threads 1

#######################################################################
# Specific Backend Directives for hdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend        hdb

#######################################################################
# Specific Backend Directives for 'other':
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
#backend        <other>
database config
#######################################################################
# Specific Directives for database #1, of type hdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        hdb

# The base of your directory in database #1
suffix          "dc=myserver,dc=somehosteddomain,dc=com"

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.
# rootdn          "cn=admin,cn=config"
rootdn          "cn=admin,dc=myserver,dc=somehosteddomain,dc=com"
# rootdn          "dc=myserver,dc=somehosteddomain,dc=com"
# rootpw          {SSHA}Afaw3o8asdAWEfksj

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# The dbconfig settings are used to generate a DB_CONFIG file the first
# time slapd starts.  They do NOT override existing an existing DB_CONFIG
# file.  You should therefore change these settings in DB_CONFIG directly
# or remove DB_CONFIG and restart slapd for changes to take effect.

# For the Debian package we use 2MB as default but be sure to update this
# value if you have plenty of RAM
dbconfig set_cachesize 0 2097152 0

# Sven Hartge reported that he had to set this value incredibly high
# to get slapd running at all. See http://bugs.debian.org/303057 for more
# information.

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500
# Number of locks (both requested and granted)
dbconfig set_lk_max_locks 1500
# Number of lockers
dbconfig set_lk_max_lockers 1500

# Indexing options for database #1
index           objectClass eq

# Save the time that the entry gets modified, for database #1
lastmod         on

# Checkpoint the BerkeleyDB database periodically in case of system
# failure and to speed slapd shutdown.
checkpoint      512 30

# Where to store the replica logs for database #1
# replogfile    /var/lib/ldap/replog

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
# acl specific for phamm

# access to doesn't like commented lines inside !!

#        by dn="cn=admin,dc=webhabitat,dc=be" write
#        by dn="cn=admin,dc=myserver,dc=somehosteddomain,dc=com" write
access to attrs=userPassword,shadowLastChange
        by anonymous auth
        by self write
        by * none

#        by dn="cn=admin,dc=yourdomain,dc=tld" write
#        by dn="cn=admin,dc=myserver,dc=somehosteddomain,dc=com" write
access to *
        by * read

access to dn.base="" by * read

# For Netscape Roaming support, each user gets a roaming
# profile for which they have write access to
#access to dn=".*,ou=Roaming,o=morsnet"
#        by dn="cn=admin,dc=yourdomain,dc=tld" write
#        by dnattr=owner write

#######################################################################
# Specific Directives for database #2, of type 'other' (can be hdb too):
# Database specific directives apply to this databasse until another
# 'database' directive occurs
#database        <other>

# The base of your directory for database #2
#suffix        "dc=debian,dc=org"


```


--------------------------------------------------------

here is a **init.ldif** file (*contains top level organization of the address book*):

```

dn: dc=myserver,dc=somehosteddomain,dc=com
objectClass: top
objectClass: dcObject
objectClass: organization
dc: myserver
o: private

dn: cn=admin,dc=myserver,dc=somehosteddomain,dc=com
objectClass: simpleSecurityObject
objectClass: organizationalRole
cn: admin
description: LDAP administrator
userPassword:: e2NyeXXXXXXXXXXXXXXXXcU5pLQQ=

dn: ou=personal,dc=myserver,dc=somehosteddomain,dc=com
objectClass: top
objectClass: organizationalUnit
ou: personal
description: Personal Addressbook

```


--------------------------------------------------------

here is a **template2.ldif** file (*Contains sample entry, 'Bob Smith' for the address book, which follows the mozillaAbPersonAlpha scheme*):
```

dn: cn=Bob Smith,ou=personal,dc=myserver,dc=somehosteddomain,dc=com
objectclass: top
objectclass: person
objectclass: organizationalPerson
objectclass: inetOrgPerson
objectclass: mozillaAbPersonAlpha
givenName: Bob
sn: Smith
cn: Bob Smith
mail: email@here.com
mozillaSecondEmail: .
mozillaNickname: .
homePhone: .
telephoneNumber: .
facsimileTelephoneNumber: .
pager: .
mobile: .
mozillaHomeStreet: .
mozillaHomeLocalityName: .
mozillaHomeState: .
mozillaHomePostalCode: .
mozillaHomeCountryName: .
mozillaHomeUrl: .
title: JobTitle
ou: BusinessDept
o: BusinessOrganization
street: BusinessStreet
l: BusinessCity
st: BusinessState
postalCode: BusinessZip
c: BusinessCountry
mozillaWorkUrl: .
mozillaCustom1: .
mozillaCustom2: .
mozillaCustom3: .
mozillaCustom4: .

```

---

### Post by sdaau on 2010-06-09
Well, some time later ...  I have moved on to Ubuntu 10.04, Thunderbird 3, and it seems the procedure above should still work.. 

(Btw, another tool that could be useful, instead of ApacheDS, is [phpLDAPadmin]("http://phpldapadmin.sourceforge.net/"), via [Creating LDAP address book entries to share - Mac OS X Hints]("http://www.macosxhints.com/article.php?story=20040111075453713"))

However, my original intent with LDAP was to have a centralized way to manage my email groups, which always end up being messed up :) 

Now, that seems to be a bit of a problem [1] [2] - as said here:
[quote="http://veejoe.net/blog/2010/02/ldap-groups-in-postfix/"]
I had always assumed that e-mail aliases were a one-to-one mapping of alias address to real destination.  Not the case: an alias can have multiple destinations.  It doesn&#8217;t just apply to LDAP alias support, either: as per the 'aliases' man page you can do

name: value1, value2, ...

In my LDAP situation, all I need to do is list the alias in the 'mailLocalAddress' attribute of which ever users need to receive mail for that alias.  Done!
[/quote]

I.e. in Thunderbird, you define a "mailing list", which is a collection of your local email addresses under an alias - the alias gets expanded when sending to list; for LDAP, correspondingly Thunderbird would have to call the LDAP server to expand the alias itself; but it seems there is no such functionality [3] (or rather, it is achieved differently - entries are tagged as belonging to a group, and then search can be performed against it [4]). 

In any case, reading through [5], I noticed a reference to this add-on for Thunderbird:
[LdapRW :: Add-ons for Thunderbird]("https://addons.mozilla.org/en-US/thunderbird/addon/91000/")

... which seems to be able to synchronize both address books and mailing lists(?) from Thunderbird. 

You'd still have to establish a LDAP server as above; but then, after installing the plugin, you can add an empty 'test' address book in Thunderbird, and then Tools / Ldap RW Preferences; and then pull the 'test' address book from the drop down, and in respect to above examples, enter: 

```

URI: ldap://myserver.somehosteddomain.com/ou=personal,dc=myserver,dc=somehosteddomain,com=org??sub?(objectclass=*)
Auth DN: cn=admin,dc=myserver,dc=somehosteddomain,dc=com
Basis for RDN: givenName

```And then click on "New" (or "Modify") ... Afterward close and restart Address Book, and then, from the "Ldap Cards Explorer" menu on the left, you will be able to see the 'test' address book; select it, enter first few characters of a search term in the search box below - and then the LDAP search results should be shown in the box below that search field.

Finally, you could do this for your "Personal address book" - and hopefully for the email lists belonging to it; as the plugin will install an option, "LdapRW Sync", when an address book entry is right-clicked - which can then write the local entry to the LDAP server... (however, I have not yet experimented much with it).. 

Cheers!

**Edit**: Here's a quick way to experiment with LdapRW Addon: 

First, on the server, create a new testing address book (and restart LDAP): 
```

echo "dn: ou=testingab,dc=myserver,dc=somehosteddomain,dc=com
objectClass: top
objectClass: organizationalUnit
ou: testingab
description: Testing Addressbook
"  > testing.ldif
sudo /etc/init.d/slapd stop
sudo slapadd -v -l testing.ldif
sudo /etc/init.d/slapd restart
rm testing.ldif

```Then, enter in LdapRW Preferences: 
```

URI: ldap://myserver.somehosteddomain.com/ou=testingab,dc=myserver,dc=somehosteddomain,com=org??sub?(objectclass=*)
Auth DN: cn=admin,dc=myserver,dc=somehosteddomain,dc=com
Basis for RDN: DisplayName

```... and save and close/reopen Address Book.. 

***Note** <s>that "Basis for RDN" is actually used for writing a local entry to the LDAP server; if 'givenName' as in the very first example is used, the write process may fail.</s> actually, that part establishes mapping, e.g. "Basis for RDN"="LastName" as property of Thunderbird entry, gets mapped to "Attribute for RDN"="sn" (surname) as property of LDAP schema; the default DisplayName-cn seems to work best ?! * 

Then you can add a local entry to test address book in Thunderbird, and then right-click it and choose 'LdapRW Sync'; if all goes well, you should be able to search via the "Ldap Cards Explorer" menu on the left, and see the newly added entry :) 

Well, with this addon, seems ApacheDS is no longer strictly necessary for moving addresses from Thunderbird to LDAP (Still not sure how it goes for groups though)... 

***Note2** Seems LdapRW can handle mailing lists - what it cannot handle, is entries that only have an email address (and no Display Name, Last Name etc) - in that case, probably best to run Thunderbird export -> abookconvert.php -> import via ApacheDS; and only after that, sync the remote LDAP address book with an empty local copy in Thunderbird (abookconvert.php possibly handles problems around cn, sn attributes)  * 



 

[1] [Viewing mailing lists in LDAP address books in Thunderbird? - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=657216")
[2] [LDAP groups in Postfix « Crossed Wires]("http://veejoe.net/blog/2010/02/ldap-groups-in-postfix/")
[3] [Bug 12409 &#8211; [LDAP] mozilla compose window should resolve LDAP mailing lists (groups)]("https://bugzilla.mozilla.org/show_bug.cgi?id=12409")
[4] [How to list exchange LDAP groups and users in Thunderbird.]("http://it.toolbox.com/blogs/locutus/how-to-list-exchange-ldap-groups-and-users-in-thunderbird-30434")
[5] [Bug 86405 &#8211; Make LDAP addressbooks editable]("https://bugzilla.mozilla.org/show_bug.cgi?id=86405")

---

### Post by sdaau on 2010-06-11
Well, after working on some changes of LdapRW - I finally managed to get my entire >500 contacts address book into LDAP from Thunderbird3 :) The patch is below (excuse the mess).. 

A few notes:
[LIST]
[*] LdapRW uses 'dump' to debug; to enable that in Thunderbird, see [https://developer.mozilla.org/en/DOM/window.dump](https://developer.mozilla.org/en/DOM/window.dump) ([http://kazhack.org/?post/2009/12/03/KompoZer-add-ons](http://kazhack.org/?post/2009/12/03/KompoZer-add-ons)) and run Thunderbird from command line, so you can see stderr messages (stderr messages should always show you javascript errors, while without them, sometimes the js error window may not be shown)
[*] LdapRW will fail on duplicate entries (i.e. those where DisplayName and email are equal) ... It will also fail on case-insensitive equality (i.e. if you have DisplayName=tim and PrimaryEmail=tim@test.com; and DisplayName=Tim and PrimaryEmail=Tim@test.com; those will be treated as duplicates and LdapRW will silently fail when encountering them) ... - for duplicates, simply erase one of them from your local address book before syncing (might want to empty the LDAP directory also in this case)
[*] ApacheDS is still useful for doublechecking on what has actually gone to the server (along with Wireshark)
[/LIST]

The patch should be able to handle same name and different emails - and it should also be able to handle mailing lists.. 

Note finally that OpenLDAP has a default limitation of 500 results returned ([http://www.openldap.org/doc/admin24/limits.html](http://www.openldap.org/doc/admin24/limits.html)), which means that ApacheDS will simply show "500+" as size of the address book if it is bigger than 500 entries - and the same will happen if you try to run: 
```

$ ldapsearch -W -D cn=admin,dc=myserver,dc=somehosteddomain,dc=com
 -b ou=testingab,dc=myserver,dc=somehosteddomain,dc=com \(cn=*\)

```from the command line at the server side.. (don't know a fix for that yet)... 

Well, hopefully, now syncing Thunderbird contacts to a central server should be easier :) 

Cheers! 

Edit: **Note** that there may still be some problems with modifications though... as in 

```

Error: modquery 64
undefined
value of naming attribute 'cn' is not present in entry

```In that case = delete old entry from server via Ldap Cards Explorer first - and only then, sync the new, local entry with the server... 

**Note** also, in respect to numbers shown as 'ldaprw debug' during sync: say you have 557 entries in address book; on first import/sync (from local to empty LDAP) there should be eventually, say, QSA 556 and QAA/QAG 557 in ldaprw debug - on subsequent syncs, there could be say QSA 556 with QSG 552 and QAA/QAG 0... 

**Note** also, to update a mailing list;
must delete it (the remote LDAP entry) via Ldap Cards Explorer first, and then sync it (either via right click on its entry as part of address book - or by running entire "LdapRW Sync" for the address book..) ... Same principle (delete either remote or local, and then sync / add to address book the remaining) can be applied for conflicting entries as well.. 


 


LdapRW.patch:
```

diff -Naur ldap_read_write-0.4.201005222007-tb.xpi_ORIG/chrome/content/abtoldap.js {dc6df62a-7051-46f3-b602-d53b56d707e0}/chrome/content/abtoldap.js
--- ldap_read_write-0.4.201005222007-tb.xpi_ORIG/chrome/content/abtoldap.js    2010-05-20 07:11:32.000000000 +0200
+++ {dc6df62a-7051-46f3-b602-d53b56d707e0}/chrome/content/abtoldap.js    2010-06-11 13:59:24.950765790 +0200
@@ -36,7 +36,7 @@
 
 
 function debugabtoldap(str){
-//  dump("abtoldap.js: " + str);
+  //dump("abtoldap.js: " + str);
 }
 
 /*
@@ -374,6 +374,15 @@
            if (attr instanceof Components.interfaces.nsIProperty){
              //if (attr.value){
                if( this[attr.name]==undefined ) continue;
+           // http://www.sudleyplace.com/LDAP/index.en.html
+           // "mozillaNickname - that attribute is not allowed within objectclass: groupOfNames, so it must be commented out."
+           // objectClassViolation (attribute 'mozillaNickname' not allowed)
+           // here it shows as "NickName"
+           debugabtoldap("  attr.name " + attr.name + "\n");
+               if( attr.name=="NickName" ) { 
+               debugabtoldap("NickName caught\n");
+               continue;
+           }
                if( oldmaillist == undefined ) {
                  this[attr.name]( Components.interfaces.nsILDAPModification.MOD_ADD | Components.interfaces.nsILDAPModification.MOD_BVALUES );
                } else {
diff -Naur ldap_read_write-0.4.201005222007-tb.xpi_ORIG/chrome/content/sync.js {dc6df62a-7051-46f3-b602-d53b56d707e0}/chrome/content/sync.js
--- ldap_read_write-0.4.201005222007-tb.xpi_ORIG/chrome/content/sync.js    2010-05-22 18:03:14.000000000 +0200
+++ {dc6df62a-7051-46f3-b602-d53b56d707e0}/chrome/content/sync.js    2010-06-11 13:59:38.174767093 +0200
@@ -35,7 +35,7 @@
  * ***** END LICENSE BLOCK ***** */
 
 function debugsync(str){
-//  dump("sync.js: " + str);
+  //dump("sync.js: " + str);
 }
 
 function dumperrors(str){
@@ -358,13 +358,19 @@
                 return {dn: gendnML(pref, currentcard), filter: "(objectclass=" + pref.maillistClassesAR[0]  + ")"};
 //                continue;
               } else {
-                // "(objectclass=inetorgperson)"
+        // "(objectclass=inetorgperson)"
                 return {dn: dn, filter: "(objectclass=" + pref.objClassesAR[0] + ")"};
               }
             } else {
               if ( currentcard.isMailList ) {
                 debugsync("iteration maillist\n");
                 maillists[currentcard.displayName] = {card: currentcard};
+                debugsync(" ih1\n");
+        var gml = gendnML(pref, currentcard);
+                debugsync(" ih2\n");
+        var gmf = "(objectclass=" + pref.maillistClassesAR[0]  + ")";
+                debugsync(" "+ gml +" - " + gmf + "\n");
+        
 //                search mailing list on ldap server
 //                may be need to remove 'dn' from cards and create gendn function for all type card
                 return {dn: gendnML(pref, currentcard), filter: "(objectclass=" + pref.maillistClassesAR[0]  + ")"};
@@ -482,10 +488,21 @@
 function genrdnML(pref, card) {
   //return pref.attrRdn + "=" + card.displayName;
   var basisRdn = card.getProperty(pref.basisRdn, "");
+  debugsync("genrdnML "+ pref + " -crd: " + card + " -brdn:" + basisRdn + "\n");
   if ( basisRdn.length > 0 ) {
-    return pref.attrRdn + "=" + card.getProperty(pref.basisRdn);  
+    //return pref.attrRdn + "=" + card.getProperty(pref.basisRdn);  // WAS TYPO HERE!
+    debugsync("genrdnMLA "+ pref.attrRdn + "=" + card.getProperty(pref.basisRdn, null) + "\n"); 
+    return pref.attrRdn + "=" + card.getProperty(pref.basisRdn, null);  
   } else {
-    throw "genrdn: basisRdn.length = 0";
+    //throw "genrdn: basisRdn.length = 0";
+    //dumperrors("genrdnA: basisRdn.length = 0" + card.getProperty("PrimaryEmail",""));
+    Components.utils.reportError("genrdnA: basisRdn.length = 0" + card.getProperty("PrimaryEmail","") + card.getProperty("DisplayName",""));
+    // for email lists, here we'd get PrimaryEmail to be 0, and sn (screen name - NO, actually surname) undefined as well
+    // however, dn/DisplayName will be defined.. 
+    var tsn = card.getProperty("sn", "");
+    if (!(tsn.length>0)) {
+        card.setProperty("sn", card.getProperty("DisplayName",""));
+    }
   }
 }
 
@@ -501,7 +518,8 @@
     return pref.attrRdn + "=" + basisRdn;
   } else {
     debugsync("genrdn: basisRdn.length=" + basisRdn.length + "\n");
-    throw "genrdn: basisRdn.length = 0";
+    //throw "genrdnB: basisRdn.length = 0";
+    Components.utils.reportError("genrdnB: basisRdn.length = 0" + "-"+card.toSource()+"-"+card.wrappedJSObject+"-"+card.getProperty( "PrimaryEmail", ""));
     return null;
   }
 }
@@ -535,7 +553,7 @@
     };
     ldap.init(attrs);
   }
-
+ 
   function genaddquery(card, addqueries) {
     var addquerycount = 0;
     return function addquery(aMsg, mdn) {
@@ -562,9 +580,10 @@
             dumperrors("addquery aborting failed: " + e + "\n");
           }
 
-          dumperrors("Error: addquery " + aMsg.errorCode + "\n" 
+          dumperrors("Error: addquery B " + aMsg.errorCode + "\n" 
                   + LdapErrorsToStr(aMsg.errorCode) + "\n"
                   + aMsg.errorMessage + "\n"
+          + card.getProperty("PrimaryEmail", "" ) + "\n"
                   + card.getProperty("dn", "") + "\n");
           return null;
         }else{
@@ -586,18 +605,80 @@
       try {
         var oldcard = Components.classes["@mozilla.org/addressbook/cardproperty;1"] .createInstance(Components.interfaces.nsIAbCard);
         var mods = CreateNSMutArray();
+
+    if (!card.getProperty("LastName", null)){
+    if (card.getProperty("DisplayName", null)) {
+    card.setProperty("LastName", card.getProperty("DisplayName", null));
+    }
+    else {
+    card.setProperty("LastName", card.getProperty("PrimaryEmail", null));    
+    card.setProperty("DisplayName", card.getProperty("PrimaryEmail", null));    
+    }
+    }
    
         var dn = card.getProperty("dn", null);
         if ( !dn ){
           //dn = pref.attrRdn + "=" + card.displayName + "," + queryURL.dn;
           dn = gendn(pref, card);
+    //Components.utils.reportError("!dn "+ dn + "-" + card.displayName);
         }
+    var sn = card.getProperty("sn", null);
+        //if ( !sn ){
+        //  //dn = pref.attrRdn + "=" + card.displayName + "," + queryURL.dn;
+        //  sn = card.displayName;
+    //  card.setProperty("sn", dn);
+    //Components.utils.reportError("!sn "+ sn + "-" + card.displayName);
+        //}
+    if ( (!dn) ) {
+    Components.utils.reportError("!sn!dn "+ sn + "-" + card.displayName);
+    }
+    if (sn) {Components.utils.reportError("sn ok"+sn);}
+
+    
+    
+    
+    
+    
+    
+    
+    
+    
+    
+    
+    
         debugsync("newcardtoldap dn=" + dn + "\n");
         mods.appendElement( CreateLDAPMod( "objectClass", pref.objClassesAR, Components.interfaces.nsILDAPModification.MOD_ADD | Components.interfaces.nsILDAPModification.MOD_BVALUES ), false );
       
         mappertoldap.map(card, mods, oldcard);
-      
-        ldap.add(queryURL, pref.binddn, gengetpassword(), genaddquery(card, [{dn: dn, mods: mods /* maybe need: , card:card */}]) );
+
+    //~ http://www.sudleyplace.com/LDAP/index.en.html
+    //~ Each Distinguished Name with both a cn= and mail=  part, must be 
+    //~ changed to a format acceptable to the LDAP server. In particular, 
+    //~ the two parts must be joined with a plus sign (instead of separated 
+    //~ by a comma) so as to create a multi-valued RDN (Relative Distinguished Name).
+    //~ ... the change I suggest allows you to have entries with 
+    //~ the same name and different email addresses.
+    //~ var dn="dn=cn=Test Name,ou=testingab,dc=xxx,dc=yyy,dc=com"; var basisRdn="ou=testingab,dc=xxx,dc=yyy,dc=com"; var re = new RegExp("cn=(.+)\,"+basisRdn, "g"); var ndn = dn.replace(re, 'cn=$1+mail=s,'+basisRdn); dump(ndn+"\n");
+    //~ 
+    
+    var dnhasmail = dn.match(/mail/);
+    var ndn = ""; 
+
+    if (!(dnhasmail)) {
+        var tmail = card.getProperty("PrimaryEmail", null); //currentcard
+        //var basisRdn = pref.genRdn(card); // **** - basisRdn like this could be "My Name" or it could be "myserver.com" !! :(
+        // then better cut only up to ",ou"
+        var re = new RegExp("cn=(.+)\,ou", "g"); //("cn=(.+)\,"+basisRdn, "g");
+        ndn = dn.replace(re, 'cn=$1+mail='+tmail+',ou'); //(re, 'cn=$1+mail='+tmail+','+basisRdn);
+        //ndn = dn.replace(/cn=([^\,]+)\,/g,'cn=$1+mail='+tmail+',');
+        debugsync("    adding mail ("+tmail+") to dn ... ");
+    } else {
+        ndn = dn;
+        debugsync("    dnhasmail ... " );
+    }
+    debugsync("  ndn=" + ndn + "\n");
+                    
+        ldap.add(queryURL, pref.binddn, gengetpassword(), genaddquery(card, [{dn: ndn, mods: mods /* maybe need: , card:card */}]) );
         if (backstatus != undefined) backstatus(QUEUEADDADD, 0);        
       } catch(e) {
         dumperrors("Error: " + e+"\n");
@@ -637,7 +718,7 @@
       if (aMsg != undefined ){
           debugsync("addquery aMsg= " + aMsg.errorCode + "\n");
         if (aMsg.errorCode != Components.interfaces.nsILDAPErrors.SUCCESS) {
-          dumperrors("Error: addquery " + aMsg.errorCode + "\n" 
+          dumperrors("Error: addquery A " + aMsg.errorCode + "\n" 
                   + LdapErrorsToStr(aMsg.errorCode) + "\n"
                   + aMsg.errorMessage + "\n"
                   + card.getProperty("dn", "") + "\n");

```

---

