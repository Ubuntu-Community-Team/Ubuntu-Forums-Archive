---
title: "3G/GSM connection using PAP authentication with Ericsson F3507G &amp; ModemManager"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by roland237 on 2010-01-12
Hi,

Yesterday, I tried to get my 3G connection up with my Lenovo Ideapad S10-2 and its built-in Ericsson 3G modem. Well, as I found out after some time of debugging, it didn't work because my network provider only accepts PAP authentication, and regardless of the configuration within NetworkManager, the ModemManager always tried CHAP authentication.

I guess this is because the dialog of selecting PAP, CHAP etc. seems only be used for pppd, but not for the internal setup of the 3G modem.

For the Ericsson (and possibly other modems), the authentication for a packet connection is done with the AT*EIAAUW command, which is hard-coded in modem-manager to use the defaults for authentication.

I patched my ModemManager to allow only PAP in the AT*EIAAUW command, and this worked out perfectly. You can find the patch below. Beware that this is certainly not something that should be included by default, only given here for reference.

Frankly, I don't know who to address to talk about a possibility to get this feature (authentication method selection) in the ModemManager in a clean fashion. I'd be happy to provide some assistance to improve the ModemManager. If someone could provide me with a hint who to talk to or what to do next.

Greetings,
Roland

For your reference: the "00010" in this case references a bit-field of 5 positions, whereas the bits mark the authentication algorithms (MS-CHAPv2, MS-CHAP, CHAP, PAP, NONE) respectively. So, 00010 enables PAP and disables the rest.

[FONT=Courier New]----------------------------------------------------------------------

[email]root@frodo:/usr/src/modemmanager-0.2.git[/email].20091014t233208.16f3e00/plugins# diff  -U 5 mm-modem-mbm.c.orig mm-modem-mbm.c
--- mm-modem-mbm.c.orig    2009-10-15  01:35:39.000000000 +0200
+++ mm-modem-mbm.c    2010-01-11 20:21:49.819500184  +0100
@@ -636,11 +636,11 @@
     g_assert (primary);
 
     if  (username || password) {
         char *command;
 
-        command =  g_strdup_printf ("*EIAAUW=%d,1,\"%s\",\"%s\"",
+        command =  g_strdup_printf  ("*EIAAUW=%d,1,\"%s\",\"%s\",00010",
                                     mm_generic_gsm_get_cid (MM_GENERIC_GSM  (self)),
                                    username ? username :  "",
                                    password ? password :  "");
 
         mm_serial_port_queue_command (primary, command, 3,  mbm_auth_done, user_data);
[/FONT]

---

### Post by pdc on 2010-01-12
thanks for this; well done;

Virgin Australia mobile broadband also needs CHAP disabled;

(unlike Virgin UK I think ....... )

in this post

[http://ubuntuforums.org/showthread.php?p=8630531](http://ubuntuforums.org/showthread.php?p=8630531)

post #14 mjneil.81 describes how he disabled CHAP in /etc/ppp/options

---

### Post by roland237 on 2010-01-13
Hi,

I think modifying /etc/ppp/options (and the PPP settings dialog of the NetworkManager) will only take effect if you run pppd. It seems, for the Ericsson module, the default is to run CDC Ethernet ("Ethernet over USB"). In this case, all the PPP and authentication stuff is handled by the 3G card, so the /etc/ppp/options will not take effect here.

Greetings,
Roland

---

### Post by alexfish on 2010-01-13
hi

this site is worth a visit

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

[PPP Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][The gnome-ppp dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][User Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")
[*][Permissions for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")
[*][Adding the initial Signal Strength to the gnome-ppp connection log ]("http://www.pcurtis.com/ubuntu-mobile.htm#signal_strength")
[/LIST]
[/LIST]

---

