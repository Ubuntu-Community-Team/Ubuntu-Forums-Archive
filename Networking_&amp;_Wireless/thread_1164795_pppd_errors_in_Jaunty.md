---
title: "pppd errors in Jaunty"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by NZJon on 2009-05-20
I have installed a "hybrid Dell" modem driver, as detailed [here]("https://help.ubuntu.com/community/DialupModemHowto/Conexant"). (See the "Conexant drivers provided by Dell (full-speed and free)" section.)

The modem appears to be working, as I an hear the dial tones, etc. during dial up attempts. However, the PPP session terminates unexpectedly, as this:

> 
jon@white:/usr/share/hsfmodem-7.80.02.03full-dellhybrid$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT086725327
--> Waiting for carrier.
ATDT086725327
CONNECT 57600 
--> Carrier detected.  Waiting for prompt.
** Lucent APX Terminal Server **
Login: 
Login: 
Login: 
Login: 
--> Looks like a login prompt.
--> Sending: jon.pawley
jon.pawley
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 218.101.97.250
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Tue May 19 21:19:20 2009
--> Pid of pppd: 17568
--> Disconnecting at Tue May 19 21:19:21 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)


"man pppd" shows that the exit code of 2 indicates an error with the options. I haven't edited the default /etc/ppp/options file, and it's contents are:

> 
# /etc/ppp/options
# 
# Originally created by Jim Knoble <jmknoble@mercury.interpath.net>
# Modified for Debian by alvar Bray <alvar@meiko.co.uk>
# Modified for PPP Server setup by Christoph Lameter <clameter@debian.org>
#
# To quickly see what options are active in this file, use this command:
#   egrep -v '#|^ *$' /etc/ppp/options

# Specify which DNS Servers the incoming Win95 or WinNT Connection should use
# Two Servers can be remotely configured
# ms-dns 192.168.1.1
# ms-dns 192.168.1.2

# Specify which WINS Servers the incoming connection Win95 or WinNT should use
# ms-wins 192.168.1.50
# ms-wins 192.168.1.51

# Run the executable or shell command specified after pppd has
# terminated the link.  This script could, for example, issue commands
# to the modem to cause it to hang up if hardware modem control signals
# were not available.
#disconnect "chat -- \d+++\d\c OK ath0 OK"

# async character map -- 32-bit hex; each bit is a character
# that needs to be escaped for pppd to receive it.  0x00000001
# represents '\x01', and 0x80000000 represents '\x1f'.
asyncmap 0

# Require the peer to authenticate itself before allowing network
# packets to be sent or received.
# Please do not disable this setting. It is expected to be standard in
# future releases of pppd. Use the call option (see manpage) to disable
# authentication for specific peers.
#auth
noauth
# ... Unfortunately, fixing this properly in the peers file
# (/etc/ppp/peers/ppp0, typically) is apparently incompatible with the
# paradigm used by gnome-system-tools and system-tools-backend for
# managing the peers files.  So in Ubuntu Feisty we change the default.

# Use hardware flow control (i.e. RTS/CTS) to control the flow of data
# on the serial port.
crtscts

# Use software flow control (i.e. XON/XOFF) to control the flow of data
# on the serial port.
#xonxoff

# Specifies that certain characters should be escaped on transmission
# (regardless of whether the peer requests them to be escaped with its
# async control character map).  The characters to be escaped are
# specified as a list of hex numbers separated by commas.  Note that
# almost any character can be specified for the escape option, unlike
# the asyncmap option which only allows control characters to be
# specified.  The characters which may not be escaped are those with hex
# values 0x20 - 0x3f or 0x5e.
#escape 11,13,ff

# Don't use the modem control lines.
#local

# Specifies that pppd should use a UUCP-style lock on the serial device
# to ensure exclusive access to the device.
lock

# Don't show the passwords when logging the contents of PAP packets.
# This is the default.
hide-password

# When logging the contents of PAP packets, this option causes pppd to
# show the password string in the log message.
#show-password

# Use the modem control lines.  On Ultrix, this option implies hardware
# flow control, as for the crtscts option.  (This option is not fully
# implemented.)
modem

# Set the MRU [Maximum Receive Unit] value to <n> for negotiation.  pppd
# will ask the peer to send packets of no more than <n> bytes. The
# minimum MRU value is 128.  The default MRU value is 1500.  A value of
# 296 is recommended for slow links (40 bytes for TCP/IP header + 256
# bytes of data).
#mru 542

# Set the interface netmask to <n>, a 32 bit netmask in "decimal dot"
# notation (e.g. 255.255.255.0).
#netmask 255.255.255.0

# Disables the default behaviour when no local IP address is specified,
# which is to determine (if possible) the local IP address from the
# hostname. With this option, the peer will have to supply the local IP
# address during IPCP negotiation (unless it specified explicitly on the
# command line or in an options file).
#noipdefault

# Enables the "passive" option in the LCP.  With this option, pppd will
# attempt to initiate a connection; if no reply is received from the
# peer, pppd will then just wait passively for a valid LCP packet from
# the peer (instead of exiting, as it does without this option).
#passive

# With this option, pppd will not transmit LCP packets to initiate a
# connection until a valid LCP packet is received from the peer (as for
# the "passive" option with old versions of pppd).
#silent

# Don't request or allow negotiation of any options for LCP and IPCP
# (use default values).
#-all

# Disable Address/Control compression negotiation (use default, i.e.
# address/control field disabled).
#-ac

# Disable asyncmap negotiation (use the default asyncmap, i.e. escape
# all control characters).
#-am

# Don't fork to become a background process (otherwise pppd will do so
# if a serial device is specified).
#-detach

# Disable IP address negotiation (with this option, the remote IP
# address must be specified with an option on the command line or in
# an options file).
#-ip

# Disable IPCP negotiation and IP communication. This option should
# only be required if the peer is buggy and gets confused by requests
# from pppd for IPCP negotiation.
#noip

# Disable magic number negotiation.  With this option, pppd cannot
# detect a looped-back line.
#-mn

# Disable MRU [Maximum Receive Unit] negotiation (use default, i.e.
# 1500).
#-mru

# Disable protocol field compression negotiation (use default, i.e.
# protocol field compression disabled).
#-pc

# Require the peer to authenticate itself using PAP.
#+pap

# Don't agree to authenticate using PAP.
#-pap

# Require the peer to authenticate itself using CHAP [Cryptographic
# Handshake Authentication Protocol] authentication.
#+chap

# Don't agree to authenticate using CHAP.
#-chap

# Disable negotiation of Van Jacobson style IP header compression (use
# default, i.e. no compression).
#-vj

# Increase debugging level (same as -d).  If this option is given, pppd
# will log the contents of all control packets sent or received in a
# readable form.  The packets are logged through syslog with facility
# daemon and level debug. This information can be directed to a file by
# setting up /etc/syslog.conf appropriately (see syslog.conf(5)).  (If
# pppd is compiled with extra debugging enabled, it will log messages
# using facility local2 instead of daemon).
#debug

# Append the domain name <d> to the local host name for authentication
# purposes.  For example, if gethostname() returns the name porsche,
# but the fully qualified domain name is porsche.Quotron.COM, you would
# use the domain option to set the domain name to Quotron.COM.
#domain <d>

# Enable debugging code in the kernel-level PPP driver.  The argument n
# is a number which is the sum of the following values: 1 to enable
# general debug messages, 2 to request that the contents of received
# packets be printed, and 4 to request that the contents of transmitted
# packets be printed.
#kdebug n

# Set the MTU [Maximum Transmit Unit] value to <n>. Unless the peer
# requests a smaller value via MRU negotiation, pppd will request that
# the kernel networking code send data packets of no more than n bytes
# through the PPP network interface.
#mtu <n>

# Set the name of the local system for authentication purposes to <n>.
# This is a privileged option. With this option, pppd will use lines in the
# secrets files which have <n> as the second field when looking for a
# secret to use in authenticating the peer. In addition, unless overridden
# with the user option, <n> will be used as the name to send to the peer
# when authenticating the local system to the peer. (Note that pppd does
# not append the domain name to <n>.)
#name <n>

# Enforce the use of the hostname as the name of the local system for
# authentication purposes (overrides the name option).
#usehostname

# Set the assumed name of the remote system for authentication purposes
# to <n>.
#remotename <n>

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.
proxyarp

# Use the system password database for authenticating the peer using
# PAP. Note: mgetty already provides this option. If this is specified
# then dialin from users using a script under Linux to fire up ppp wont work.
# login

# If this option is given, pppd will send an LCP echo-request frame to the
# peer every n seconds. Normally the peer should respond to the echo-request
# by sending an echo-reply. This option can be used with the
# lcp-echo-failure option to detect that the peer is no longer connected.
lcp-echo-interval 30

# If this option is given, pppd will presume the peer to be dead if n
# LCP echo-requests are sent without receiving a valid LCP echo-reply.
# If this happens, pppd will terminate the connection.  Use of this
# option requires a non-zero value for the lcp-echo-interval parameter.
# This option can be used to enable pppd to terminate after the physical
# connection has been broken (e.g., the modem has hung up) in
# situations where no hardware modem control lines are available.
lcp-echo-failure 4

# Set the LCP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#lcp-restart <n>

# Set the maximum number of LCP terminate-request transmissions to <n>
# (default 3).
#lcp-max-terminate <n>

# Set the maximum number of LCP configure-request transmissions to <n>
# (default 10).
#lcp-max-configure <n>

# Set the maximum number of LCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#lcp-max-failure <n>

# Set the IPCP restart interval (retransmission timeout) to <n>
# seconds (default 3).
#ipcp-restart <n>

# Set the maximum number of IPCP terminate-request transmissions to <n>
# (default 3).
#ipcp-max-terminate <n>

# Set the maximum number of IPCP configure-request transmissions to <n>
# (default 10).
#ipcp-max-configure <n>

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
#ipcp-max-failure <n>

# Set the PAP restart interval (retransmission timeout) to <n> seconds
# (default 3).
#pap-restart <n>

# Set the maximum number of PAP authenticate-request transmissions to
# <n> (default 10).
#pap-max-authreq <n>

# Set the maximum time that pppd will wait for the peer to authenticate
# itself with PAP to <n> seconds (0 means no limit).
#pap-timeout <n>

# Set the CHAP restart interval (retransmission timeout for
# challenges) to <n> seconds (default 3).
#chap-restart <n>

# Set the maximum number of CHAP challenge transmissions to <n>
# (default 10).
#chap-max-challenge

# If this option is given, pppd will rechallenge the peer every <n>
# seconds.
#chap-interval <n>

# With this option, pppd will accept the peer's idea of our local IP
# address, even if the local IP address was specified in an option.
#ipcp-accept-local

# With this option, pppd will accept the peer's idea of its (remote) IP
# address, even if the remote IP address was specified in an option.
#ipcp-accept-remote

# Disable the IPXCP and IPX protocols.
# To let pppd pass IPX packets comment this out --- you'll probably also
# want to install ipxripd, and have the Internal IPX Network option enabled
# in your kernel.  /usr/doc/HOWTO/IPX-HOWTO.gz contains more info.
noipx

# Exit once a connection has been made and terminated. This is the default,
# unless the `persist' or `demand' option has been specified.
#nopersist

# Do not exit after a connection is terminated; instead try to reopen
# the connection.
#persist

# Terminate after n consecutive failed connection attempts.
# A value of 0 means no limit. The default value is 10.
#maxfail <n>

# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.
#demand

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  Note: it is not advisable to use this option with the persist
# option without the demand option.  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
#idle <n>

# Specifies how many seconds to wait before re-initiating the link after
# it terminates.  This option only has any effect if the persist or demand
# option is used.  The holdoff period is not applied if the link was
# terminated because it was idle.
#holdoff <n>

# Wait for up n milliseconds after the connect script finishes for a valid
# PPP packet from the peer.  At the end of this time, or when a valid PPP
# packet is received from the peer, pppd will commence negotiation by
# sending its first LCP packet.  The default value is 1000 (1 second).
# This wait period only applies if the connect or pty option is used.
#connect-delay <n>

# Packet filtering: for more information, see pppd(8)
# Any packets matching the filter expression will be interpreted as link
# activity, and will cause a "demand" connection to be activated, and reset
# the idle connection timer. (idle option)
# The filter expression is akin to that of tcpdump(1)
#active-filter <filter-expression>

# ---<End of File>---


I have also noticed that during the boot-up phase of my laptop, something is attempting to initialise a dial-up/PPP connection, which I really wouldn't expect.

Does anyone have any suggestions as to what I could try?

Many thanks,

   Jon

---

### Post by GeorgeVita on 2009-05-21
Hi **NZJon**,
post here your /etc/wvdial.conf file.

Regards,
George

---

### Post by NZJon on 2009-05-24
Hi George,

Thanks for your reply, and sorry I haven't replied sooner.. I have to ferry stuff between work and home, which is making my life a little bit slow... ;)

My /etc/wvdial.conf contains the following:

> 
[Dialer Defaults]
Phone = 086725327
Username = blahblah
Password = blah
New PPPD = yes


As far as I can tell, that's pretty innocuous, and I can't see what would cause pppd to exit with exit code 2.

Thanks for your help though.

   Jon

---

### Post by GeorgeVita on 2009-05-25
Hi Jon, some ideas:

- first try to add a line to your /etc/wvdial.conf file: **Stupid Mode = 1**
(just in case the "automatic" ppp login will work)

- if still not connected try to set MTU to 1524 (if this number comes from your provider as shown at your log) or search/ask to find appropriate. To setup this you have to uncomment line #mtu <n> and make it: **mtu 1524** (sudo gedit /etc/ppp/options)

EDIT: Also try to connect with Ethernet & Wireless disabled (in case of a conflick that you did not realise).
sudo ifconfig eth0 down
sudo ifconfig wlan0 down


Regards,
George

---

### Post by ferebee on 2009-05-28
I haven't tried Jaunty yet (cd is in the mail!), but in Intrepid, the only way I could get wvdial or gnome-ppp to stay connected were  to run them through sudo (or gksudo in gnome-ppp's case). I know this isn't recommended, security wise, but that's the only way I could stay connected without getting this error message:
> --> Starting pppd at Tue May 19 21:19:20 2009
--> Pid of pppd: 17568
--> Disconnecting at Tue May 19 21:19:21 2009
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2) 

I can't remember the exact problem now, but I think it had to do with the regular user not having the correct permissions to dial out.

---

