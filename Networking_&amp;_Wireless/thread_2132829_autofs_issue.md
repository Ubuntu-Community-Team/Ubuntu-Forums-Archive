---
title: "autofs issue"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by manopj1 on 2013-04-06
I use ubuntu 11.04 client
In my autofs is working fine .I use ldap server and needs to mount users homedir.I use nfs to mount homedir.if I specify username in auto.home manually it works fine.When I use wild cards instead of username the home directoy not mounting

test 192.168.5.1:/export/users/test - working
* 192.168.5.1:/export/users/&  and when i tried to login with test username its not working.
Kinldy give me a solution

---

### Post by manopj1 on 2013-04-12
my /etc/default file looks like below

#
# Define default options for autofs.
#
# MASTER_MAP_NAME - default map name for the master map.
#
MASTER_MAP_NAME="/etc/auto.master"
#
# TIMEOUT - set the default mount timeout (default 600).
#
TIMEOUT=300
#
# NEGATIVE_TIMEOUT - set the default negative timeout for
#              failed mount attempts (default 60).
#
NEGATIVE_TIMEOUT=10
#
# MOUNT_WAIT - time to wait for a response from umount(8).
#            Setting this timeout can cause problems when
#            mount would otherwise wait for a server that
#            is temporarily unavailable, such as when it's
#            restarting. The defailt of waiting for mount(8)
#            usually results in a wait of around 3 minutes.
#
#MOUNT_WAIT=-1
#
# UMOUNT_WAIT - time to wait for a response from umount(8).
#
#UMOUNT_WAIT=12
#
# BROWSE_MODE - maps are browsable by default.
#
BROWSE_MODE="yes"
#
# MOUNT_NFS_DEFAULT_PROTOCOL - specify the default protocol used by
#                    mount.nfs(8). Since we can't identify
#                    the default automatically we need to
#                    set it in our configuration. This will
#                    only make a difference for replicated
#                    map entries as availability probing isn't
#                    used for single host map entries.
#
MOUNT_NFS_DEFAULT_PROTOCOL=3
#
# APPEND_OPTIONS - append to global options instead of replace.
#
#APPEND_OPTIONS="yes"
#
# LOGGING - set default log level "none", "verbose" or "debug"
#
#LOGGING="none"
#
# Define server URIs
#
# LDAP_URI - space seperated list of server uris of the form
#          <proto>://<server>[/] where <proto> can be ldap
#          or ldaps. The option can be given multiple times.
#          Map entries that include a server name override
#          this option.
#
#         This configuration option can also be used to
#         request autofs lookup SRV RRs for a domain of
#         the form <proto>:///[<domain dn>]. Note that a
#         trailing "/" is not allowed when using this form.
#         If the domain dn is not specified the dns domain
#         name (if any) is used to construct the domain dn
#         for the SRV RR lookup. The server list returned
#         from an SRV RR lookup is refreshed according to
#         the minimum ttl found in the SRV RR records or
#         after one hour, whichever is less.
#
#LDAP_URI="192.168.5.250"
#
# LDAP__TIMEOUT - timeout value for the synchronous API  calls
#          (default is LDAP library default).
#
#LDAP_TIMEOUT=-1
#
# LDAP_NETWORK_TIMEOUT - set the network response timeout (default 8).
#
#LDAP_NETWORK_TIMEOUT=8
#
# Define base dn for map dn lookup.
#
# SEARCH_BASE - base dn to use for searching for map search dn.
#         Multiple entries can be given and they are checked
#         in the order they occur here.
#
#SEARCH_BASE=""
#
# Define the LDAP schema to used for lookups
#
# If no schema is set autofs will check each of the schemas
# below in the order given to try and locate an appropriate
# basdn for lookups. If you want to minimize the number of
# queries to the server set the values here.
#
#MAP_OBJECT_CLASS="nisMap"
#ENTRY_OBJECT_CLASS="nisObject"
#MAP_ATTRIBUTE="nisMapName"
#ENTRY_ATTRIBUTE="cn"
#VALUE_ATTRIBUTE="nisMapEntry"
#
# Other common LDAP nameing
#
#MAP_OBJECT_CLASS="automountMap"
#ENTRY_OBJECT_CLASS="automount"
#MAP_ATTRIBUTE="ou"
#ENTRY_ATTRIBUTE="cn"
#VALUE_ATTRIBUTE="automountInformation"
#
#MAP_OBJECT_CLASS="automountMap"
#ENTRY_OBJECT_CLASS="automount"
#MAP_ATTRIBUTE="automountMapName"
#ENTRY_ATTRIBUTE="automountKey"
#VALUE_ATTRIBUTE="automountInformation"
#
# AUTH_CONF_FILE - set the default location for the SASL
#               authentication configuration file.
#
#AUTH_CONF_FILE="/etc/autofs_ldap_auth.conf"
#
# MAP_HASH_TABLE_SIZE - set the map cache hash table size.
#             Should be a power of 2 with a ratio roughly
#             between 1:10 and 1:20 for each map.
#
#MAP_HASH_TABLE_SIZE=1024
#
# General global options
#
# If the kernel supports using the autofs miscellanous device
# and you wish to use it you must set this configuration option
# to "yes" otherwise it will not be used.
USE_MISC_DEVICE="yes"
#
#OPTIONS=""
#
anything i need to change on this

---

### Post by steeldriver on 2013-04-12
I don't use LDAP but I do use autofs with home wildcards and it works fine for me (12.04, autofs5 version 5.0.6-0ubuntu5.1)

```
$ cat /etc/auto.master
+auto.master
# configure nfs automount (for ad-hoc connection to local NAS)
/nfs/home   /etc/auto.nfs --timeout=120 --ghost

$ cat /etc/auto.nfs
# configure nfs automount (for ad hoc connection to local NAS)
*** -fstype=nfs,soft,intr,rsize=8192,wsize=8192,nosuid,tcp 192.168.1.127:/c/home/&**
```

So I suspect it is a problem with your LDAP configuration rather than your autofs configuration - sorry that's all I've got

---

### Post by manopj1 on 2013-04-15
thanks four your reply.I am also new to ldap. Instead of this * and & if i use ldap username i is working fine. I dont't know why this is not taking.

---

