---
title: "Dial up and pidgin / evolution"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by curaloucura on 2009-09-15
Hello Everyone

I have a Smartlink dial up modem configured and working on a fresh installation of Ubuntu Jaunty, internet is fine on Firefox and apt-get for example, but I can't get pidgin, thunderbird and evolution to work. It always display a message of trying to connect and then time out. I use wvdial to connect. Psi works fine. It's strange that just after I installed the drivers and configured my connection pidgin was working, but after a reboot it did not work again. 
I read somewhere else to disable network-manager, but even unchecking network, I get the same timeout problem.

Any clue of what's happening?


Cheers

Anderson

---

### Post by jdripper on 2009-09-15
Which mail server are you trying to connect to with thubderbird/evolution ? Can you ping that server?
That would be what you have for POP/IMAP or SMTP.

For pidgin, under "help" you'll see "debug window" click that and a small window will open.
Try to disconnect/reconnect with that open and past the messages in here.
Otherwise if it doesn't even open, run on a terminal window :
pidgin -d

Then paste the messages in here. That should give us a fairly good idea of why it doesn't connect.

---

### Post by curaloucura on 2009-09-17
Hello and thanks for you help

Before start, I found out an interesting thing

if I run on shell

#telnet [www.gmail.com](www.gmail.com) 80

or

#ssh myserver
(to test the port 22)

it works, but if I try

#telnet pop.gmail.com 995

it keeps trying to reach the server

if I do the same on my ubuntu machine here at office, it works, so it seems my ubuntu can't use those ports for some reason with the dial up connection. 


Here my pidgin debug window, nothing relevent it seems:

(23:33:03) util: Writing file prefs.xml to directory /home/anderson/.purple
(23:33:03) util: Writing file /home/anderson/.purple/prefs.xml
(23:33:03) util: Writing file accounts.xml to directory /home/anderson/.purple
(23:33:03) util: Writing file /home/anderson/.purple/accounts.xml
(23:33:03) util: Writing file blist.xml to directory /home/anderson/.purple
(23:33:03) util: Writing file /home/anderson/.purple/blist.xml

And on Pidgin status I have the message: "Waiting for network connection",
I am trying to connect to gtalk so I selected that option when adding my account


About Thunderbird, it's a gmail account, I used the default wizard for gmail. 

On status bar, it says for few seconds "Looking up pop.gmail.com" then changes to "Connecting to pop.gmail.com".

My settings are:
pop.gmail.com port 995 SSL


After a while I get a pop up message:
"Connection to server pop.gmail.com timed out"


the whole pidgin -d, not the window debug is the following:

anderson@freegan:~$ pidgin -d
(19:51:32) prefs: Reading /home/anderson/.purple/prefs.xml
(19:51:32) prefs: Finished reading /home/anderson/.purple/prefs.xml
(19:51:32) dbus: okkk
(19:51:32) plugins: probing /usr/lib/pidgin/extplacement.so
(19:51:32) plugins: probing /usr/lib/pidgin/xmppconsole.so
(19:51:32) plugins: probing /usr/lib/pidgin/timestamp_format.so
(19:51:32) plugins: probing /usr/lib/pidgin/iconaway.so
(19:51:32) plugins: probing /usr/lib/pidgin/pidgin-otr.so
(19:51:32) plugins: probing /usr/lib/pidgin/ticker.so
(19:51:32) plugins: probing /usr/lib/pidgin/pidginrc.so
(19:51:32) plugins: probing /usr/lib/pidgin/spellchk.so
(19:51:32) plugins: probing /usr/lib/pidgin/timestamp.so
(19:51:32) plugins: probing /usr/lib/pidgin/musicmessaging.so
(19:51:32) plugins: probing /usr/lib/pidgin/gevolution.so
(19:51:32) plugins: probing /usr/lib/pidgin/gestures.so
(19:51:32) plugins: probing /usr/lib/pidgin/convcolors.so
(19:51:32) plugins: probing /usr/lib/pidgin/sendbutton.so
(19:51:32) plugins: probing /usr/lib/pidgin/history.so
(19:51:32) plugins: probing /usr/lib/pidgin/markerline.so
(19:51:32) plugins: probing /usr/lib/pidgin/cap.so
(19:51:32) plugins: probing /usr/lib/pidgin/notify.so
(19:51:32) plugins: probing /usr/lib/pidgin/nautilus.so
(19:51:32) plugins: probing /usr/lib/pidgin/gtkbuddynote.so
(19:51:32) plugins: probing /usr/lib/purple-2/libbonjour.so
(19:51:32) plugins: probing /usr/lib/purple-2/pidgin-libnotify.so
(19:51:32) plugins: probing /usr/lib/purple-2/libzephyr.so
(19:51:32) plugins: probing /usr/lib/purple-2/idle.so
(19:51:32) plugins: probing /usr/lib/purple-2/tcl.so
(19:51:32) plugins: /usr/lib/purple-2/tcl.so is not loadable: libtk8.4.so.0: cannot open shared object file: No such file or directory
(19:51:32) plugins: probing /usr/lib/purple-2/libyahoo.so
(19:51:32) plugins: probing /usr/lib/purple-2/buddynote.so
(19:51:32) plugins: probing /usr/lib/purple-2/libqq.so
(19:51:32) plugins: probing /usr/lib/purple-2/libsimple.so
(19:51:32) plugins: probing /usr/lib/purple-2/libnovell.so
(19:51:32) plugins: probing /usr/lib/purple-2/libsilcpurple.so
(19:51:32) plugins: probing /usr/lib/purple-2/libmyspace.so
(19:51:32) plugins: probing /usr/lib/purple-2/perl.so
(19:51:32) plugins: probing /usr/lib/purple-2/offlinemsg.so
(19:51:32) plugins: probing /usr/lib/purple-2/libaim.so
(19:51:32) plugins: probing /usr/lib/purple-2/dbus-example.so
(19:51:32) plugins: probing /usr/lib/purple-2/psychic.so
(19:51:32) plugins: probing /usr/lib/purple-2/libicq.so
(19:51:32) plugins: probing /usr/lib/purple-2/ssl.so
(19:51:32) plugins: probing /usr/lib/purple-2/libmsn.so
(19:51:32) plugins: probing /usr/lib/purple-2/log_reader.so
(19:51:32) plugins: probing /usr/lib/purple-2/newline.so
(19:51:32) plugins: probing /usr/lib/purple-2/autoaccept.so
(19:51:32) plugins: probing /usr/lib/purple-2/statenotify.so
(19:51:32) plugins: probing /usr/lib/purple-2/libxmpp.so
(19:51:32) util: Reading file xmpp-caps.xml from directory /home/anderson/.purple
(19:51:32) jabber: creating hash tables for data objects
(19:51:32) plugins: probing /usr/lib/purple-2/libsametime.so
(19:51:32) plugins: /usr/lib/purple-2/libsametime.so has a prefs_info, but is a prpl. This is no longer supported.
(19:51:32) plugins: probing /usr/lib/purple-2/liboscar.so
(19:51:32) plugins: /usr/lib/purple-2/liboscar.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:51:32) plugins: probing /usr/lib/purple-2/libirc.so
(19:51:32) plugins: probing /usr/lib/purple-2/libgg.so
(19:51:32) plugins: probing /usr/lib/purple-2/joinpart.so
(19:51:32) plugins: probing /usr/lib/purple-2/ssl-nss.so
(19:51:32) plugins: probing /usr/lib/purple-2/libjabber.so
(19:51:32) plugins: /usr/lib/purple-2/libjabber.so is not usable because the 'purple_init_plugin' symbol could not be found.  Does the plugin call the PURPLE_INIT_PLUGIN() macro?
(19:51:32) prefs: /purple/status/scores/offline changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/available changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/invisible changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/away changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/extended_away changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/idle changed, scheduling save.
(19:51:32) prefs: /purple/status/scores/offline_msg changed, scheduling save.
(19:51:32) util: Reading file accounts.xml from directory /home/anderson/.purple
(19:51:32) util: Reading file status.xml from directory /home/anderson/.purple
(19:51:32) certificate: CertificateVerifier x509, singleuse requested but not found.
(19:51:32) certificate: CertificateVerifier singleuse registered
(19:51:32) certificate: CertificatePool x509, ca requested but not found.
(19:51:32) certificate: CertificateScheme x509 requested but not found.
(19:51:32) certificate/x509/ca: Lazy init failed because an X.509 Scheme is not yet registered. Maybe it will be better later.
(19:51:32) certificate/x509/ca: Init failed, probably because a dependency is not yet registered. It has been deferred to later.
(19:51:32) certificate: CertificatePool ca registered
(19:51:32) certificate: CertificatePool x509, tls_peers requested but not found.
(19:51:32) certificate: CertificatePool tls_peers registered
(19:51:32) certificate: CertificateVerifier x509, tls_cached requested but not found.
(19:51:32) certificate: CertificateVerifier tls_cached registered
(19:51:32) prefs: /purple/logging/format changed, scheduling save.
(19:51:32) prefs: /purple/logging/format changed, scheduling save.
(19:51:32) prefs: /purple/proxy/type changed, scheduling save.
(19:51:32) prefs: /purple/proxy/host changed, scheduling save.
(19:51:32) prefs: /purple/proxy/port changed, scheduling save.
(19:51:32) prefs: /purple/proxy/username changed, scheduling save.
(19:51:32) prefs: /purple/proxy/password changed, scheduling save.
(19:51:32) certificate: CertificateScheme x509 requested but not found.
(19:51:32) certificate: CertificateScheme x509 registered
(19:51:32) util: Reading file smileys.xml from directory /home/anderson/.purple
(19:51:32) util: File /home/anderson/.purple/smileys.xml does not exist (this is not necessarily an error)
(19:51:32) stun: using server 
(19:51:32) sound: Initializing sound output drivers.
(19:51:32) prefs: /pidgin/conversations/placement changed, scheduling save.
(19:51:32) util: Reading file blist.xml from directory /home/anderson/.purple
(19:51:32) plugins: Loading saved plugin /usr/lib/purple-2/pidgin-libnotify.so
(19:51:32) plugins: Loading saved plugin /usr/lib/purple-2/ssl-nss.so
(19:51:32) plugins: Loading saved plugin /usr/lib/pidgin/nautilus.so
(19:51:32) nautilus: saved blist online
(19:51:32) plugins: Loading saved plugin /usr/lib/purple-2/ssl.so
(19:51:32) pounce: Error reading pounces: Failed to open file '/home/anderson/.purple/pounces.xml': No such file or directory
(19:51:32) ui_main: Failed to load the default window icon (scalablepx version)!
(19:51:32) Session Management: ICE initialized.
(19:51:32) Session Management: Connecting with no previous ID
(19:51:32) Session Management: Handling new ICE connection... 
(19:51:32) done.
(19:51:32) Session Management: Connected to manager (gnome-session) with client ID 10c578c2cbbd792f6125314149270386500000031600035
(19:51:32) Session Management: Using pidgin as command
(19:51:33) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(19:51:33) dbus: The signal "gtkblist-unhiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(19:51:33) account: Network not connected; skipping reconnect
(19:51:33) Session Management: Received first save_yourself
(19:51:33) Session Management: Received save_complete
(19:51:33) gtkblist: added visibility manager: 1
(19:51:37) util: Writing file prefs.xml to directory /home/anderson/.purple
(19:51:37) util: Writing file /home/anderson/.purple/prefs.xml
(19:51:37) util: Writing file accounts.xml to directory /home/anderson/.purple
(19:51:37) util: Writing file /home/anderson/.purple/accounts.xml
(19:51:37) util: Writing file blist.xml to directory /home/anderson/.purple
(19:51:37) util: Writing file /home/anderson/.purple/blist.xml
(20:15:20) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(20:15:25) util: Writing file prefs.xml to directory /home/anderson/.purple
(20:15:25) util: Writing file /home/anderson/.purple/prefs.xml
(20:15:25) util: Writing file accounts.xml to directory /home/anderson/.purple
(20:15:25) util: Writing file /home/anderson/.purple/accounts.xml
(20:51:56) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(20:52:01) util: Writing file prefs.xml to directory /home/anderson/.purple
(20:52:01) util: Writing file /home/anderson/.purple/prefs.xml
(20:52:01) util: Writing file accounts.xml to directory /home/anderson/.purple
(20:52:01) util: Writing file /home/anderson/.purple/accounts.xml
(20:56:56) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(20:57:01) util: Writing file prefs.xml to directory /home/anderson/.purple
(20:57:01) util: Writing file /home/anderson/.purple/prefs.xml
(20:57:01) util: Writing file accounts.xml to directory /home/anderson/.purple
(20:57:01) util: Writing file /home/anderson/.purple/accounts.xml
(20:57:32) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(20:57:37) util: Writing file prefs.xml to directory /home/anderson/.purple
(20:57:37) util: Writing file /home/anderson/.purple/prefs.xml
(20:57:37) util: Writing file accounts.xml to directory /home/anderson/.purple
(20:57:37) util: Writing file /home/anderson/.purple/accounts.xml
(21:04:31) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(21:04:36) util: Writing file prefs.xml to directory /home/anderson/.purple
(21:04:36) util: Writing file /home/anderson/.purple/prefs.xml
(21:04:36) util: Writing file accounts.xml to directory /home/anderson/.purple
(21:04:36) util: Writing file /home/anderson/.purple/accounts.xml
(21:08:07) prefs: /purple/savedstatus/isidleaway changed, scheduling save.
(21:08:12) util: Writing file prefs.xml to directory /home/anderson/.purple
(21:08:12) util: Writing file /home/anderson/.purple/prefs.xml
(21:08:12) util: Writing file accounts.xml to directory /home/anderson/.purple
(21:08:12) util: Writing file /home/anderson/.purple/accounts.xml
(21:08:21) dbus: Need to register an object with the dbus subsystem. (If you are not a developer, please ignore this message.)
(21:08:21) dbus: The signal "gtkblist-hiding" caused some dbus error. (If you are not a developer, please ignore this message.)
(21:08:21) prefs: /pidgin/blist/list_visible changed, scheduling save.
(21:08:26) util: Writing file prefs.xml to directory /home/anderson/.purple
(21:08:26) util: Writing file /home/anderson/.purple/prefs.xml

---

### Post by curaloucura on 2009-09-19
bump

---

### Post by curaloucura on 2009-09-20
Funny

The problem with smtp was that my internet provider just didn't work on port 995.
When I tried to dial to a different provider, it worked fine.

About the pidgin, I found this issue

[http://developer.pidgin.im/ticket/9702](http://developer.pidgin.im/ticket/9702)


Now everything is fine  =)

---

