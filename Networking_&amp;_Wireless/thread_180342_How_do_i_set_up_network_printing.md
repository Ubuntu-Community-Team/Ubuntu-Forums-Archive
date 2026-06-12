---
title: "How do i set up network printing"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2006-05-22
Hey i have two computer running ubuntu 5.10 and they are networked and share files but i want to share printer the computer with the printer has a cannon i550 usb printer and its ip is 192.168.1.100 and the computer that i want ot be able to print from ip is 192.168.1.101

---

### Post by jonny on 2006-05-22
First you need to go to printer administration and configure both computers to automatically detect LAN printers.  That's the easy bit.

Next you need to edit the configuration file for CUPS, the printing system - it's /etc/cups/cupsd.conf (you might want to take a copy of the old file before you begin hacking).  Look for a section that lists the network addresses from which CUPS will allow connections, and add your local network addresses.

When you've done that, restart CUPS (sudo /etc/init.d/cupsysd restart or restart your PC) and the printer should be available for use.

---

### Post by CameronCalver on 2006-05-22
im not sure where is it can you go into it take a chunk out of it and post it and when i have done that on both computer what do i do under System--Admin-Printing on the computer with the printer do i make a network printer but what do ido for url

---

### Post by jonny on 2006-05-22
I don't have a linux PC to hand to look at the config file - perhaps someone else can give detailed advice.

You shouldn't need to enter a url anywhere except in that one file.  When network printer autodetection is working, all PCs will automatically see all available network printers.  It's extremely slick - once you've got it working.

---

### Post by jonny on 2006-05-22
You need to change the Locations section.  Mine looks like this:
```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.11.0/24
</Location>
```That means that it will accept anthing on the 192.168.11.* network.  You might need to change this according to your network settings.

---

### Post by CameronCalver on 2006-05-24
ok when i have  done that on both computers.
On the computer that has the printer connected to it do i make a netowkr primnter but do i type in for url

---

### Post by Jose Catre-Vandis on 2006-05-26
I have a similar requirement. 2 x PC with Ubuntu on a LAN

I can see the networked printer in printer settings on the remote machine, and the machine with the printer prints OK. When I go to print on the remote machine, it starts off OK but then the remote machine grinds to a halt, everything goes on a mega go slow and nothing is printed, and nothing shows in the printer window. A hard reset is the only way out. What gives?

[edit]
Seems that asking to print on the client sends my wireless usb adapter into a spin (prism2/3 linux-wlan-ng), giving an error on connections and repeatedly trying, which maxes out the CPU

[2nd edit]

OK, got this fixed now. Was running Hoary, so updated to Breezy. replaced all edited config files like cupsd and gdm when asked. Network printer was already in printers after install (not sure if this was a new find or from before) test print worked immediately without any further configuration and the later version of wlan-ng seems to have got itself sorted out with regards to CPU maxing. According to the howtos this shouldn't work but it does! My two cupsd.confs listed below to help.

**Server** (my LAN addressing is 10.10.10.*)(I have RunAsUser set to No because I use a pdf printer in cups)
```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser No
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.10.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location> 
```

**Client** (this I presume is the default cupsd.conf for Breezy)
```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.
#
#   Copyright 1997-2005 by Easy Software Products, all rights reserved.
#
#   These coded instructions, statements, and computer programs are the
#   property of Easy Software Products and are protected by Federal
#   copyright law.  Distribution and use rights are outlined in the file
#   "LICENSE.txt" which should have been included with this file.  If this
#   file is missing or damaged please contact Easy Software Products
#   at:
#
#       Attn: CUPS Licensing Information
#       Easy Software Products
#       44141 Airport View Drive, Suite 204
#       Hollywood, Maryland 20636 USA
#
#       Voice: (301) 373-9600
#       EMail: cups-info@cups.org
#         WWW: http://www.cups.org
#

########################################################################
#                                                                      #
# This is the CUPS configuration file.  If you are familiar with       #
# Apache or any of the other popular web servers, we've followed the   #
# same format.  Any configuration variable used here has the same      #
# semantics as the corresponding variable in Apache.  If we need       #
# different functionality then a different name is used to avoid       #
# confusion...                                                         #
#                                                                      #
########################################################################


########
######## Server Identity
########

#
# ServerName: the hostname of your server, as advertised to the world.
# By default CUPS will use the hostname of the system.
#
# To set the default server used by clients, see the client.conf file.
#

#ServerName myhost.domain.com

#
# ServerAdmin: the email address to send all complaints/problems to.
# By default CUPS will use "root@hostname".
#

#ServerAdmin root@your.domain.com


########
######## Server Options
########

#
# ConfigFilePerm: permissions of configuration files like
# /etc/cups/printer.conf.
#

ConfigFilePerm 0600

#
# AccessLog: the access log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/access_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#AccessLog /var/log/cups/access_log

#
# Classification: the classification level of the server.  If set, this
# classification is displayed on all pages, and raw printing is disabled.
# The default is the empty string.
#

#Classification classified
#Classification confidential
#Classification secret
#Classification topsecret
#Classification unclassified

#
# ClassifyOverride: whether to allow users to override the classification
# on printouts. If enabled, users can limit banner pages to before or
# after the job, and can change the classification of a job, but cannot
# completely eliminate the classification or banners.
#
# The default is off.
#

#ClassifyOverride off

#
# DataDir: the root directory for the CUPS data files.
# By default "/usr/share/cups".
#

#DataDir /usr/share/cups

#
# DefaultCharset: the default character set to use. If not specified,
# defaults to "utf-8".  Note that this can also be overridden in
# HTML documents...
#

DefaultCharset notused

#
# DefaultLanguage: the default language if not specified by the browser.
# If not specified, the current locale is used.
#

#DefaultLanguage en

#
# DocumentRoot: the root directory for HTTP documents that are served.
# By default "/usr/share/cups/doc-root".
#

#DocumentRoot /usr/share/cups/doc-root

#
# ErrorLog: the error log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/error_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#ErrorLog /var/log/cups/error_log

#
# FileDevice: determines whether the scheduler will allow new printers
# to be added using device URIs of the form "file:/foo/bar". The default
# is not to allow file devices due to the potential security vulnerability
# and due to the fact that file devices do not support raw printing.
#

#FileDevice No


#
# FontPath: the path to locate all font files (currently only for pstoraster)
# By default "/usr/share/cups/fonts".
#

#FontPath /usr/share/cups/fonts

#
# LogLevel: controls the number of messages logged to the ErrorLog
# file and can be one of the following:
#
#     debug2	Log everything.
#     debug	Log almost everything.
#     info      Log all requests and state changes.
#     warn      Log errors and warnings.
#     error     Log only errors.
#     none      Log nothing.
#

LogLevel info

#
# MaxLogSize: controls the maximum size of each log file before they are
# rotated.  Defaults to 1048576 (1MB).  Set to 0 to disable log rotating.
#

#MaxLogSize 0

#
# PageLog: the page log file; if this does not start with a leading /
# then it is assumed to be relative to ServerRoot.  By default set to
# "/var/log/cups/page_log"
#
# You can also use the special name "syslog" to send the output to the
# syslog file or daemon.
#

#PageLog /var/log/cups/page_log

#
# PreserveJobHistory: whether or not to preserve the job history after a
# job is completed, cancelled, or stopped.  Default is Yes.
#

#PreserveJobHistory Yes

#
# PreserveJobFiles: whether or not to preserve the job files after a
# job is completed, cancelled, or stopped.  Default is No.
#

#PreserveJobFiles No

#
# AutoPurgeJobs: automatically purge jobs when not needed for quotas.
# Default is No.
#

#AutoPurgeJobs No

#
# MaxCopies: maximum number of copies that a user can request. Default is
# 100.
#

#MaxCopies 100

#
# MaxJobs: maximum number of jobs to keep in memory (active and completed.)
# Default is 500; the value 0 is used for no limit.
#

#MaxJobs 500

#
# MaxJobsPerPrinter: maximum number of active jobs per printer. The default
# is 0 for no limit.
#

#MaxJobsPerPrinter 0

#
# MaxJobsPerUser: maximum number of active jobs per user. The default
# is 0 for no limit.
#

#MaxJobsPerUser 0

#
# MaxPrinterHistory: controls the maximum number of history collections
# in the printer-state-history attribute.  Set to 0 to disable history
# data.
#

#MaxPrinterHistory 10

#
# Printcap: the name of the printcap file.  Default is /etc/printcap.
# Leave blank to disable printcap file generation.
#

Printcap /var/run/cups/printcap

#
# PrintcapFormat: the format of the printcap file, currently either
# BSD or Solaris.  The default is "BSD".
#

#PrintcapFormat BSD
#PrintcapFormat Solaris

#
# PrintcapGUI: the name of the GUI options panel program to associate
# with print queues under IRIX.  The default is "/usr/bin/glpoptions"
# from ESP Print Pro.
#
# This option is only used under IRIX; the options panel program
# must accept the "-d printer" and "-o options" options and write
# the selected printer options back to stdout on completion.
#

#PrintcapGUI /usr/bin/glpoptions

#
# RequestRoot: the directory where request files are stored.
# By default "/var/spool/cups".
#

#RequestRoot /var/spool/cups

#
# RemoteRoot: the name of the user assigned to unauthenticated accesses
# from remote systems.  By default "remroot".
#

#RemoteRoot remroot

#
# ServerBin: the root directory for the scheduler executables.
# By default "/usr/lib/cups".
#

#ServerBin /usr/lib/cups

#
# ServerRoot: the root directory for the scheduler.
# By default "/etc/cups".
#

#ServerRoot /etc/cups


#
# ServerTokens: specifies what information in provided in the Server
# header of HTTP responses. The default is Minor.
#
# ServerTokens None
# ServerTokens ProductOnly       CUPS
# ServerTokens Major             CUPS/1
# ServerTokens Minor             CUPS/1.1
# ServerTokens Minimal           CUPS/1.1.23
# ServerTokens OS                CUPS/1.1.23 (uname)
# ServerTokens Full              CUPS/1.1.23 (uname) IPP/1.1
#

#ServerTokens Minor


########
######## Fax Support
########

#
# FaxRetryLimit: the number of times a fax job is retried.
# The default is 5 times.
#

#FaxRetryLimit 5

#
# FaxRetryInterval: the number of seconds between fax job retries.
# The default is 300 seconds/5 minutes.
#

#FaxRetryInterval 300


########
######## Encryption Support
########

#
# ServerCertificate: the file to read containing the server's certificate.
# Defaults to "/etc/cups/ssl/server.crt".
#

#ServerCertificate /etc/cups/ssl/server.crt

#
# ServerKey: the file to read containing the server's key.
# Defaults to "/etc/cups/ssl/server.key".
#

#ServerKey /etc/cups/ssl/server.key


########
######## Filter Options
########

#
# User/Group: the user and group the server runs under.  Normally this
# must be cupsys and lpadmin, however you can configure things for another
# user or group as needed.
#
# Note: the server must be run initially as root to support the
# default IPP port of 631.  It changes users whenever an external
# program is run, or if the RunAsUser directive is specified...
#

#User cupsys
#Group lpadmin

#
# RunAsUser: The RunAsUser directive controls whether the scheduler runs as the
# unpriviledged user account (usually cupsys). The default is No which
# leaves the scheduler running as the root user. However, the Debian package
# was prepared to work as user cupsys, which greatly reduces the impact of
# security holes.
#
# Note: Running as a non-priviledged user may prevent LPD and locally connected
# printers from working due to permission problems. The lpd backend will
# automatically use a non-priviledged mode that is not 100% compliant with RFC
# 1179. The parallel, serial, and usb backends will need write access to the
# corresponding device files.
#

RunAsUser Yes

#
# RIPCache: the amount of memory that each RIP should use to cache
# bitmaps.  The value can be any real number followed by "k" for
# kilobytes, "m" for megabytes, "g" for gigabytes, or "t" for tiles
# (1 tile = 256x256 pixels.)  Defaults to "8m" (8 megabytes).
#

#RIPCache 8m

#
# TempDir: the directory to put temporary files in.  This directory must be
# writable by the user defined above!  Defaults to "/var/spool/cups/tmp" or
# the value of the TMPDIR environment variable.
#

#TempDir /var/spool/cups/tmp

#
# FilterLimit: sets the maximum cost of all job filters that can be run
# at the same time.  A limit of 0 means no limit.  A typical job may need
# a filter limit of at least 200; limits less than the minimum required
# by a job force a single job to be printed at any time.
#
# The default limit is 0 (unlimited).
#

#FilterLimit 0

########
######## Network Options
########

#
# Ports/addresses that we listen to.  The default port 631 is reserved
# for the Internet Printing Protocol (IPP) and is what we use here.
#
# You can have multiple Port/Listen lines to listen to more than one
# port or address, or to restrict access:
#
#    Port 80
#    Port 631
#    Listen hostname
#    Listen hostname:80
#    Listen hostname:631
#    Listen 1.2.3.4
#    Listen 1.2.3.4:631
# 
# NOTE: Unfortunately, most web browsers don't support TLS or HTTP Upgrades
# for encryption.  If you want to support web-based encryption you'll
# probably need to listen on port 443 (the "https" port...)
#
# NOTE 2: In order for the command-line and web interfaces to work, you
# must have at least one Port or Listen line that allows access from the
# local loopback address (localhost).
#

#Port 80
#Port 443
#Port 631
#
Listen 127.0.0.1:631

#
# HostNameLookups: whether or not to do lookups on IP addresses to get a
# fully-qualified hostname.  This defaults to Off for performance reasons...
#

#HostNameLookups On

#
# KeepAlive: whether or not to support the Keep-Alive connection
# option.  Default is on.
#

#KeepAlive On

#
# KeepAliveTimeout: the timeout before Keep-Alive connections are
# automatically closed.  Default is 60 seconds.
#

#KeepAliveTimeout 60

#
# MaxClients: controls the maximum number of simultaneous clients that
# will be handled.  Defaults to 100.
#

#MaxClients 100

#
# MaxClientsPerHost: controls the maximum number of simultaneous clients that
# will be handled from a specific host.  Defaults to 10 or 1/10th of the
# MaxClients setting, whichever is larger.  A value of 0 specifies the
# automatic (10 or 1/10th) setting.
#

#MaxClientsPerHost 0

#
# MaxRequestSize: controls the maximum size of HTTP requests and print files.
# Set to 0 to disable this feature (defaults to 0.)
#

#MaxRequestSize 0

#
# Timeout: the timeout before requests time out.  Default is 300 seconds.
#

#Timeout 300


########
######## Browsing Options
########

#
# Browsing: whether or not to broadcast and/or listen for CUPS printer
# information on the network. For Ubuntu, this setting has been externalized to
# a separate configuration file cupsd-browsing.conf. This allows to change the
# browsing setting with /usr/share/cups/enable_browsing (or manually) without
# modifying this main configuration file, which avoids dpkg questions on
# conffile upgrades.

Include cupsd-browsing.conf

#
# BrowseProtocols: which protocols to use for browsing.  Can be
# any of the following separated by whitespace and/or commas:
#
#     all  - Use all supported protocols.
#     cups - Use the CUPS browse protocol.
#     slp  - Use the SLPv2 protocol.
#
# The default is "cups".
#
# NOTE: If you choose to use SLPv2, it is *strongly* recommended that
#       you have at least one SLP Directory Agent (DA) on your
#       network.  Otherwise, browse updates can take several seconds,
#       during which the scheduler will not respond to client
#       requests.
#

#BrowseProtocols cups

#
# BrowseAddress: specifies a broadcast address to be used.  By
# default browsing information is not sent!
#
# Note: HP-UX does not properly handle broadcast unless you have a
# Class A, B, C, or D netmask (i.e. no CIDR support).
#
# Note: Using the "global" broadcast address (255.255.255.255) will
# activate a Linux demand-dial link with the default configuration.
# If you have a LAN as well as the dial-up link, use the LAN's
# broadcast address.
#
# The @LOCAL address broadcasts to all non point-to-point interfaces.
# For example, if you have a LAN and a dial-up link, @LOCAL would
# send printer updates to the LAN but not to the dial-up link.
# Similarly, the @IF(name) address sends to the named network
# interface, e.g. @IF(eth0) under Linux.  Interfaces are refreshed
# automatically (no more than once every 60 seconds), so they can
# be used on dynamically-configured interfaces, e.g. PPP, 802.11, etc.
#

#BrowseAddress x.y.z.255
#BrowseAddress x.y.255.255
#BrowseAddress x.255.255.255
#BrowseAddress 255.255.255.255
BrowseAddress @LOCAL
#BrowseAddress @IF(name)

#
# BrowseShortNames: whether or not to use "short" names for remote printers
# when possible (e.g. "printer" instead of "printer@host".)  Enabled by
# default.
#

#BrowseShortNames Yes

#
# BrowseAllow: specifies an address mask to allow for incoming browser
# packets. The default is to allow packets from all addresses.
#
# BrowseDeny: specifies an address mask to deny for incoming browser
# packets. The default is to deny packets from no addresses.
#
# Both "BrowseAllow" and "BrowseDeny" accept the following notations for
# addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#     @LOCAL
#     @IF(name)
#
# The hostname/domainname restrictions only work if you have turned hostname
# lookups on!
#

#BrowseAllow address
#BrowseDeny address

#
# BrowseInterval: the time between browsing updates in seconds.  Default
# is 30 seconds.
#
# Note that browsing information is sent whenever a printer's state changes
# as well, so this represents the maximum time between updates.
#
# Set this to 0 to disable outgoing broadcasts so your local printers are
# not advertised but you can still see printers on other hosts.
#

#BrowseInterval 30

#
# BrowseOrder: specifies the order of BrowseAllow/BrowseDeny comparisons.
#

#BrowseOrder allow,deny
#BrowseOrder deny,allow

#
# BrowsePoll: poll the named server(s) for printers
#

#BrowsePoll address:port

#
# BrowsePort: the port used for UDP broadcasts.  By default this is
# the IPP port; if you change this you need to do it on all servers.
# Only one BrowsePort is recognized.
#

#BrowsePort 631

#
# BrowseRelay: relay browser packets from one address/network to another.
#

#BrowseRelay source-address destination-address
#BrowseRelay @IF(src) @IF(dst)

#
# BrowseTimeout: the timeout for network printers - if we don't
# get an update within this time the printer will be removed
# from the printer list.  This number definitely should not be
# less the BrowseInterval value for obvious reasons.  Defaults
# to 300 seconds.
#

#BrowseTimeout 300

#
# ImplicitClasses: whether or not to use implicit classes.
#
# Printer classes can be specified explicitly in the classes.conf
# file, implicitly based upon the printers available on the LAN, or
# both.
#
# When ImplicitClasses is On, printers on the LAN with the same name
# (e.g. Acme-LaserPrint-1000) will be put into a class with the same
# name. This allows you to setup multiple redundant queues on a LAN
# without a lot of administrative difficulties.  If a user sends a
# job to Acme-LaserPrint-1000, the job will go to the first available
# queue.
#
# Enabled by default.
#

#ImplicitClasses On

#
# ImplicitAnyClasses: whether or not to create "AnyPrinter" implicit
# classes.
#
# When ImplicitAnyClasses is On and a local queue of the same name
# exists, e.g. "printer", "printer@server1", "printer@server1", then
# an implicit class called "Anyprinter" is created instead.
#
# When ImplicitAnyClasses is Off, implicit classes are not created
# when there is a local queue of the same name.
#
# Disabled by default.
#

#ImplicitAnyCLasses Off

#
# HideImplicitMembers: whether or not to show the members of an
# implicit class.
#
# When HideImplicitMembers is On, any remote printers that are
# part of an implicit class are hidden from the user, who will
# then only see a single queue even though many queues will be
# supporting the implicit class.
#
# Enabled by default.
#

#HideImplicitMembers On


########
######## Security Options
########

#
# SystemGroup: the group name for "System" (printer administration)
# access.  The default varies depending on the operating system, but
# will be "sys", "system", or "root" (checked for in that order.)
#
# Debian: The default CUPS group is "lpadmin".
#

#SystemGroup lpadmin

#
# RootCertDuration: How frequently the root certificate is regenerated.
# Defaults to 300 seconds.
#

#RootCertDuration 300

#
# Access permissions for each directory served by the scheduler.
# Locations are relative to DocumentRoot...
#
# AuthType: the authorization to use:
#
#    None   - Perform no authentication
#    Basic  - Perform authentication using the HTTP Basic method.
#    Digest - Perform authentication using the HTTP Digest method.
#
#    (Note: local certificate authentication can be substituted by
#           the client for Basic or Digest when connecting to the
#           localhost interface)
#
# AuthClass: the authorization class; currently only "Anonymous", "User",
# "System" (valid user belonging to group SystemGroup), and "Group"
# (valid user belonging to the specified group) are supported.
#
# AuthGroupName: the group name for "Group" authorization.
#
# Order: the order of Allow/Deny processing.
#
# Allow: allows access from the specified hostname, domain, IP address,
# network, or interface.
#
# Deny: denies access from the specified hostname, domain, IP address,
# network, or interface.
#
# Both "Allow" and "Deny" accept the following notations for addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#     @LOCAL
#     @IF(name)
#
# The host and domain address require that you enable hostname lookups
# with "HostNameLookups On" above.
#
# The @LOCAL address allows or denies from all non point-to-point
# interfaces.  For example, if you have a LAN and a dial-up link,
# @LOCAL could allow connections from the LAN but not from the dial-up
# link.  Similarly, the @IF(name) address allows or denies from the
# named network interface, e.g. @IF(eth0) under Linux.  Interfaces are
# refreshed automatically (no more than once every 60 seconds), so
# they can be used on dynamically-configured interfaces, e.g. PPP,
# 802.11, etc.
#
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library and scheduler.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".
#

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

#<Location /classes>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /classes/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

<Location /jobs>
#
# You may wish to limit access to job operations, either with Allow
# and Deny lines, or by requiring a username and password.
#
AuthType Basic
AuthClass User
</Location>

#<Location /printers>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /printers/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#

## Anonymous access (default)
#AuthType None

## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User

## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User

## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#</Location>

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

AuthType Basic
AuthClass System

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

#Encryption Required
</Location>

#
#

```

---

### Post by pizzipie on 2006-05-26
[quote=Jose Catre-Vandis]I have a similar requirement. 2 x PC with Ubuntu on a LAN

I can see the networked printer in printer settings on the remote machine, and the machine with the printer prints OK. When I go to print on the remote machine, it starts off OK but then the remote machine grinds to a halt, everything goes on a mega go slow and nothing is printed, and nothing shows in the printer window. A hard reset is the only way out. What gives?[/quote]

Along this same sort of topic: I have a pc (gateway) direct connect to epson and remote connect to (hp). And a laptop (hp) direct connect to desktop remote connect to epson. Each computer can ping the other and I can read files from one to the other etc. When I print to the remote printer (either computer) the print job stats says for example:

Active          User            Title                   Printer                State             Size(kb)
1                 rick            Test Page             Deskjet-812C     pending           15

I can't get the printers to print files even though it appears the files have been delivered to the remote printer correctly.

Thakns in advance for help in getting print job printed.

RP

---

### Post by CameronCalver on 2006-05-26
can people stop taking over my thread plz

on the computer with the printer connected to it do i make a network printer but what do i type in for the url

---

### Post by Jose Catre-Vandis on 2006-05-27
[QUOTE=CameronCalver]can people stop taking over my thread plz

on the computer with the printer connected to it do i make a network printer but what do i type in for the url[/QUOTE]

Sorry, CameronCalver, but we all seem to have the same problem (although I admit pizzipie is a bit offtopic), so I am sure you would be happy to share the solution, if a linux/ubuntu guru can provide the answer. Also our additional posts help to bring the thread back to the fore.......:-D

---

### Post by CameronCalver on 2006-05-27
Ok all i want ot know is on the computer with the printer connected to it do i make a netowkr printer and if so whatg do i type in as the url

---

### Post by Iowan on 2006-05-28
For the machine on which the printer is connected, the setting should be **local**. There won't be a URL, but a port instead. (but I've been wrong before...)

---

### Post by CameronCalver on 2006-05-28
ok i made a printer on the the computer with the printer but it did not comeup on the other computer so i have a spare old printer so  iconnected it up to the other computer and made a printer and now it work but it is on the wrong computer i want the good printer share how will i fix that?

hang on i fixed it now on the computer without a printeri can make a network printer and after url i just type 192.168.1.100 coz thats the computer with the printers ip and then it makes that printer on the computer with a printer but when i go to print to it it just says 1 job then after properties it says 

Printing: Network host '192.168.1.100' is busy; will retry in 30 seconds...

---

### Post by Boelcke on 2006-05-28
I got mine to work (printing from a client ubuntu pc to a server ubuntu pc) by using the IP address.  That is:

At the PC where I'm sending the file from, I put in the IP address in /etc/cups/client.conf.  Add, "ServerName 192.168.1.100." Found that at: [http://occy.net/printing](http://occy.net/printing).

I've got that working, but my files may be slightly different than yours.  I made them match:
[https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu)
with the exception of adding the ServerName line.

Once I did that (and restarted both CUPS servers, on the client and the server, "sudo /etc/init.d/cupsys restart"), I hit System, Administration, Printing, and the printer appeared.  In that Printers window, under Global Settings, make sure you've checked Detect LAN Printers.

My open question is:
The computer with the printer attached (the server) sometimes changes its IP address (it gets it from DHCP).  What's the format for putting the hostname in there (after ServerName) as the name of the computer, rather than the IP?  I can't seem to get that to work...

---

### Post by Iowan on 2006-05-30
[QUOTE=Boelcke]
My open question is:
The computer with the printer attached (the server) sometimes changes its IP address (it gets it from DHCP).  What's the format for putting the hostname in there (after ServerName) as the name of the computer, rather than the IP?  I can't seem to get that to work...[/QUOTE]

Here's a link to having clients send theri hostname to DHCP server - will that help?
[http://www.ubuntuforums.org/showthread.php?t=177832]("http://www.ubuntuforums.org/showthread.php?t=177832")

---

### Post by jonny on 2006-05-31
Been away from this thread for a while.  Here's a recap of how I did it:

1. Set up the server (the computer with a physical connection) to use the printer.  You can use the standard Gnome Add Printer tool to do this, and you need to set it up as a local printer.  Print a test page to prove it works.

2. Using the Gnome tool, enable autodetection of LAN printers on the server.

3. Edit /etc/cups/cupsd.conf on the server as I described in Post 5 above.  Make sure that you change the 192.168.11.0/24 to reflect your network settings (for 99% of home networks, you leave the /24 bit exactly as it is; it's the other numbers that you need to change)

4. Restart CUPS on the server (sudo /etc/init.d/cupsysd restart) and print another test page

5. On the client, use the Gnome tools to enable autodetection of LAN printers.

6. On the client, close the printer setup window and reopen it.  Your remote printer should have appeared automatically, so print a test page to check it out.

Those steps worked perfectly for me on a home network of 4 ubuntu PCs running a mixture of Dapper and Breezy.

Where do you get problems?  Do you receive any error messages or are my instructions insufficiently clear at some point?

---

### Post by Boelcke on 2006-05-31
jonny, I'm almost there!  I think I've been mixing advice from multiple places and confusing the issue.  So, I reset all my cups files (cupsd.conf, client.conf) back to the way they were intitially, and followed your advice.

In your example, you had:
```
Allow from 192.168.11.0/24
```
My router is set to assign IP addresses numbering up from 192.168.1.100.  For example, right now my "server" computer is 192.168.1.101, and the "client" computer is 192.168.1.102.  So, I added this line to /etc/cups/cupsd.conf:
```
Allow from 192.168.1.0/24
```
Is this right?  No new printers appeared in my client's System,Administration,Printers window.  I had tried 192.168.1.* before, but that didn't seem to do anything.  Finally, in desperation to gain some understanding, I just tried
```
Allow from 192.168.1.102
```
which is the current address of the client computer.

No luck, no new printer in the window.

1. Is there something else I might be doing wrong?

2. Can I "Add New Printer" the thing?  It doesn't seem like the optimum way to run a CUPS server, but for my small network, it'd be OK.  But, there's no network printers detected, and I'm really not sure what to put in the URI anyway.

Thanks in advance for all the great help.

---

### Post by CameronCalver on 2006-05-31
Hey i know this is on breezy 5.10 thread but i upgraded to dapper on both computers and you said you networked dapper and breezy .
In my cupsd.conf files it does no have the Allow thing this is the the client cupsd.conf

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#


and this is the server

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#


i also edited my etc/cups/cups.d/ports.conf and browse.conf so could some1 post me there so ican fix because when i go into printing it says cups could not be contacted

---

### Post by pizzipie on 2006-06-01
[quote=Jose Catre-Vandis]Sorry, CameronCalver, but we all seem to have the same problem (although I admit pizzipie is a bit offtopic), so I am sure you would be happy to share the solution, if a linux/ubuntu guru can provide the answer. Also our additional posts help to bring the thread back to the fore.......:-D[/quote]

Sorry, Jose, if I seem "offtopic".  I have been floundering around trying to set up printers on a network but all  fails. I did get two computers to talk to each other but when I tried to get printing going all that happened was one computer's desktop got wiped out.

Please advise where I should go to address this problem.

Thanks, pizzipie

---

### Post by mancho42 on 2006-06-02
Apologies for butting in - I originally posted another on-topic cry for help here - then suddenly my problem seemed to go away!

Now I'm out of time and can't figger out how to delete this entry - so apologies again.

---

### Post by CameronCalver on 2006-06-02
Hey i know this is on breezy 5.10 thread but i upgraded to dapper on both computers and you said you networked dapper and breezy .
In my cupsd.conf files it does no have the Allow thing this is the the client cupsd.conf

#
#
# Sample configuration file for the Common UNIX Printing System (CUPS)
# scheduler. See "man cupsd.conf" for a complete description of this
# file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
Order allow,deny
Allow localhost
Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
Order allow,deny
Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
AuthType Basic
Require user @SYSTEM
Order allow,deny
Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
# Job-related operations must be done by the owner or an adminstrator...
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

# All administration operations require an adminstrator to authenticate...
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
AuthType Basic
Require user @SYSTEM
Order deny,allow
</Limit>

# Only the owner or an administrator can cancel or authenticate a job...
<Limit Cancel-Job CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

<Limit All>
Order deny,allow
</Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#


and this is the server

#
#
# Sample configuration file for the Common UNIX Printing System (CUPS)
# scheduler. See "man cupsd.conf" for a complete description of this
# file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
Order allow,deny
Allow localhost
Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
Order allow,deny
Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
AuthType Basic
Require user @SYSTEM
Order allow,deny
Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
# Job-related operations must be done by the owner or an adminstrator...
<Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

# All administration operations require an adminstrator to authenticate...
<Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
AuthType Basic
Require user @SYSTEM
Order deny,allow
</Limit>

# Only the owner or an administrator can cancel or authenticate a job...
<Limit Cancel-Job CUPS-Authenticate-Job>
Require user @OWNER @SYSTEM
Order deny,allow
</Limit>

<Limit All>
Order deny,allow
</Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#


i also edited my etc/cups/cups.d/ports.conf and browse.conf so could some1 post me there so ican fix because when i go into printing it says cups could not be contacted

---

### Post by jonny on 2006-06-02
The problem appears to be with the config file on the server - you haven't updated it in accordance with post #5.  Look at this section:
```
# Restrict access to the server...
<Location />
Order allow,deny
Allow localhost
Allow @LOCAL
</Location>
```
That's telling CUPS to ignore all requests unless they come from the local computer - but you want it to accept connections from any computer on your local network.

As for your corrupted etc/cups/cups.d/ports.conf and browse.conf, I'd suggest renaming them and then reinstalling CUPS (use Synaptic to do this).  This is a useful trick to remember - the standard ubuntu behaviour is for reinstallation of a package to replace missing configuration files but to not overwrite any existing files.

---

### Post by CameronCalver on 2006-06-02
Ok i did what everyone said and nothing worked so i plugged in my spare printer into my other computer and made a printer enbale lan and everything and guess what it was sharing it but i dont want to share the printer from that computer i want to share the printer on the server 

This is the conf file from the server

 Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.1.120
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>


and this is the conf file from the computer that i want to be able to connect to the printer



  Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.1.110
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

---

### Post by Niber on 2006-10-19
check in the /etc/cups/cups.d/ports.conf, that you have the following line inthere:
Listen 192.168.1.100:631 #the servers nic

---

