---
title: "Network Manager from CVS installed; how do I use WPA?"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by Jeff250 on 2006-01-23
Hi, I installed the latest Network Manager from CVS according to this guide:
[https://wiki.ubuntu.com/NetworkManager](https://wiki.ubuntu.com/NetworkManager)
I've heard that this version is supposed to support WPA, yet I don't see any option for it in the applet (only WEP options), and I cannot connect to my WPA network.  I have wpa_supplicant installed too, which is already configured to connect to my network.  How can I use the WPA support in the latest Network Manager?  Thanks.

---

### Post by Lambert on 2006-01-23
I didn't see anything on their site or in their change log. The TODO List still has it listed.

> Any of these items are of course fair game for anyone, patches are greatly welcome.  It also serves as a "what still needs to be done" list.


- WPA support

WPA support is greatly, significantly, mightily needed.


> * NetworkManager
   * Initscripts are now generated
   * Not waiting as long for scans to complete (Bill Moss).
   * Fix several D-BUS object leaks (John Palmieri, Dan Williams,
                                     Christopher Aillon)
   * VPN now advertises state changes
   * Make --without-named work (j@bootlab.org)
   * Make --with-dhcdbd work correctly (j@bootlab.org)
   * Fix timeout scan values (Bill Moss)
   * Send notifications of device strength changing so clients do
     not have to poll.
   * Don't return a UDI device if it doesn't exist (Tomislav Vujec)
   * Strip whitespace from the VPN banner (Bill Moss)
   * VPN Manager rewritten to better support signals (Dan Williams)
   * Don't allow clients to determine what states we should be
     scanning in, add logic to scan when we need to.
   * Blacklist some common ESSIDs such that multiple access points
     with these ESSIDs aren't treated as the same network.
   * Support for D-BUS enabled named (Dan Williams)
   * Only '#' is a valid comment in resolv.conf (Robert Love)
   * Don't try to set auth mode on the AP from the allowed list if
     it's NULL (Bill Moss)
   * Add internal scanning code so we don't have to use iwlib's
     code any longer (Dan Williams)
   * libnm now uses guints instead of gints for its callback IDs.
   * libnm_glib_unregister_callback () now works.
   * Fix our scanning interval (Robert Love)
   * Updates to backends for Gentoo, SuSE, RedHat, Debian, and
     Slackware (Robert Love, Peter Jones, Bill Nottingham,
                [email]j@bootlab.org[/email])
       - Dialup support in RedHat backend
       - ISDN support in SUSE backend
       - Other fixes

* nm-applet
   * The applet is no longer threaded (Dan Williams)
   * Dialogs no longer block the UI when shown
   * Passphrase dialog now treats Esc keypresses properly
   * Create Network and Connect to Network dialogs now have
     different window titles
   * New icons for connecting to a network and to a VPN
     (Diana Fong)
   * Context menu items have been cleaned up
   * Pressing enter in the passphrase entry should activate the
     default action.
   * Fix icon animation smoothness
   * Display more data in the Connection Information dialog
     (Robert Love)


---

### Post by pangloss on 2006-01-24
What driver are you using? My understanding was that most drivers needed a little work in order to advertise the wireless extension capabilities correctly. e.g. for ipw2100, see: [http://sourceforge.net/mailarchive/forum.php?thread_id=9425988&forum_id=38938]("http://sourceforge.net/mailarchive/forum.php?thread_id=9425988&forum_id=38938")

---

### Post by quietglow on 2006-01-24
I'm lucky enough to have that very wireless card, but I'm not sure how to apply that patch. If someone can enlighten me, I'd be appreciative. If it works with WPA, I could also potentially build a deb for it if there was an interest.

---

### Post by zachtib on 2006-01-24
any word on wpa with the atheros drivers?

---

### Post by Lambert on 2006-01-24
[quote=zachtib]any word on wpa with the atheros drivers?[/quote]

madwifi works with wpa_supplicant, can you not get it working?

[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)

---

### Post by Jeff250 on 2006-01-24
Ah hah!  OK, I've the WPA option to appear.  I have the IPW2200 chip, so I just took the latest drivers and hand-applied the patch that pangloss linked to, installed them, and now it's appearing properly.  Unfortunately, now I'm getting a supplicant error when I try to connect to my network (WPA1-TKIP).  I've got the latest wpa_supplicant from cvs installed, so this may take some more playing around with yet.

---

### Post by Jeff250 on 2006-01-24
OK, I applied the patch attached to this email to the latest wpa_supplicant from CVS:
[http://lists.shmoo.com/pipermail/hostap/2006-January/012321.html](http://lists.shmoo.com/pipermail/hostap/2006-January/012321.html)

I compiled it, installed it, and my supplicant error went away.  I am posting this from a WPA connection made by Network Manager!

---

### Post by zachtib on 2006-01-25
[QUOTE=Lambert]madwifi works with wpa_supplicant, can you not get it working?

[http://madwifi.org/wiki/UserDocs/802.11i](http://madwifi.org/wiki/UserDocs/802.11i)[/QUOTE]
no, i haven't been able to connect to my schools network in linux.

for that matter, I've never been able to connect to any encrypted wireless network at all in Ubuntu

EDIT:  HUZZAH! switching to the madwifi-ng drivers solved all of my problems with wpa_supplicant, but how to I connect to a wpa network with networkmanager?

---

### Post by Jeff250 on 2006-01-25
Update:  wpa_supplicant cvs has been updated to include the patch that I linked to earlier.

zachtib, it requires installing the latest Network Manger from cvs and the latest  wpa_supplicant from cvs.  This last part isn't so difficult, but you'll also need compatible drivers.  (Being compatible with just wpa_supplicant isn't enough.)  The only drivers that I know are working correctly so far with Network Manager WPA are the latest ipw2100 or ipw2200, but even these require the patch to which pangloss linked.

---

### Post by zachtib on 2006-01-26
[QUOTE=Jeff250]Update:  wpa_supplicant cvs has been updated to include the patch that I linked to earlier.

zachtib, it requires installing the latest Network Manger from cvs and the latest  wpa_supplicant from cvs.  This last part isn't so difficult, but you'll also need compatible drivers.  (Being compatible with just wpa_supplicant isn't enough.)  The only drivers that I know are working correctly so far with Network Manager WPA are the latest ipw2100 or ipw2200, but even these require the patch to which pangloss linked.[/QUOTE]

great...
connecting via a command line is a pain, but at least it works at all.

I guess I'll just wait patiently for better drivers

also, I couldn't seem to build networkmanager from CVS, i tried to, but something broke

```
zach@notapowerbook:~/dev/NetworkManager$ make
make  all-recursive
make[1]: Entering directory `/home/zach/dev/NetworkManager'
Making all in utils
make[2]: Entering directory `/home/zach/dev/NetworkManager/utils'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/zach/dev/NetworkManager/utils'
Making all in src
make[2]: Entering directory `/home/zach/dev/NetworkManager/src'
Making all in named-manager
make[3]: Entering directory `/home/zach/dev/NetworkManager/src/named-manager'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/zach/dev/NetworkManager/src/named-manager'
Making all in vpn-manager
make[3]: Entering directory `/home/zach/dev/NetworkManager/src/vpn-manager'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/zach/dev/NetworkManager/src/vpn-manager'
Making all in dhcp-manager
make[3]: Entering directory `/home/zach/dev/NetworkManager/src/dhcp-manager'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/zach/dev/NetworkManager/src/dhcp-manager'
Making all in backends
make[3]: Entering directory `/home/zach/dev/NetworkManager/src/backends'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/zach/dev/NetworkManager/src/backends'
make[3]: Entering directory `/home/zach/dev/NetworkManager/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I../src/named-manager -I../src/vpn-manager -I../src/dhcp-manager -I../utils -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_VERSION_MAJOR=0 -DDBUS_VERSION_MINOR=36 -DDBUS_VERSION_MICRO=2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -DDBUS_API_SUBJECT_TO_CHANGE -DG_DISABLE_DEPRECATED -DBINDIR=\"/usr/local/bin\" -DDATADIR=\"/usr/local/share\" -DSYSCONFDIR=\"/usr/local/etc\" -DARP_DEBUG    -g -O2 -MT NetworkManager-NetworkManagerDevice.o -MD -MP -MF ".deps/NetworkManager-NetworkManagerDevice.Tpo" \
  -c -o NetworkManager-NetworkManagerDevice.o `test -f 'NetworkManagerDevice.c' || echo './'`NetworkManagerDevice.c; \
then mv -f ".deps/NetworkManager-NetworkManagerDevice.Tpo" ".deps/NetworkManager-NetworkManagerDevice.Po"; \
else rm -f ".deps/NetworkManager-NetworkManagerDevice.Tpo"; exit 1; \
fi
NetworkManagerDevice.c: In function ‘process_scan_results’:
NetworkManagerDevice.c:4571: error: ‘IW_EV_POINT_OFF’ undeclared (first use in this function)
NetworkManagerDevice.c:4571: error: (Each undeclared identifier is reported only once
NetworkManagerDevice.c:4571: error: for each function it appears in.)
NetworkManagerDevice.c:4683: warning: pointer targets in passing argument 2 of ‘nm_ap_set_wpa_ie’ differ in signedness
NetworkManagerDevice.c:4686: warning: pointer targets in passing argument 2 of ‘nm_ap_set_rsn_ie’ differ in signedness
NetworkManagerDevice.c:4713: warning: pointer targets in passing argument 2 of ‘hexstr2bin’ differ in signedness
NetworkManagerDevice.c:4715: warning: pointer targets in passing argument 2 of ‘nm_ap_set_wpa_ie’ differ in signedness
NetworkManagerDevice.c:4717: warning: pointer targets in passing argument 2 of ‘nm_ap_set_rsn_ie’ differ in signedness
make[3]: *** [NetworkManager-NetworkManagerDevice.o] Error 1
make[3]: Leaving directory `/home/zach/dev/NetworkManager/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/zach/dev/NetworkManager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zach/dev/NetworkManager'
make: *** [all] Error 2
```

---

### Post by Cableless on 2006-01-26
I'm trying to compile the CVS version of Network Manager on Dapper.  I have gnome-common installed with all the build-deps for network-manager.  However I have a compile error.

When running:
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var

I get:
Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found

blah@blah:~/NetworkManager$ slocate libtool.m4
/usr/share/aclocal/libtool.m4
/usr/share/libtool/libtool.m4

Whats the problem here?

---

### Post by Cableless on 2006-01-26
Never mind.  I missed the missing automake at the top of the output.  Installed automake 1.9 and all is well.

---

### Post by kaamos on 2006-01-28
I keep getting these when compiling from CVS:
```
...
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../include -I../../utils -I../../src -I../../src/named-manager -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDBUS_VERSION_MAJOR=0 -DDBUS_VERSION_MINOR=36 -DDBUS_VERSION_MICRO=2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -g -Wall -DDBUS_API_SUBJECT_TO_CHANGE -DG_DISABLE_DEPRECATED -DBINDIR=\"/usr/bin\" -DDATADIR=\"/usr/share\" -DSYSCONFDIR=\"/etc\" -Wall -Werror -std=gnu89 -g -O2 -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wdeclaration-after-statement -Wfloat-equal -Wno-unused-parameter -Wno-sign-compare -MT libvpn_manager_la-nm-vpn-connection.lo -MD -MP -MF .deps/libvpn_manager_la-nm-vpn-connection.Tpo -c nm-vpn-connection.c  -fPIC -DPIC -o .libs/libvpn_manager_la-nm-vpn-connection.o
cc1: warnings being treated as errors
In file included from ../../src/NetworkManagerMain.h:28,
                 from ../../src/NetworkManagerDbusUtils.h:31,
                 from nm-dbus-vpn.h:25,
                 from nm-vpn-connection.c:25:
/usr/include/hal/libhal.h:295: warning: declaration of 'index' shadows a global declaration
/usr/include/string.h:304: warning: shadowed declaration is here
make[3]: *** [libvpn_manager_la-nm-vpn-connection.lo] Error 1
make[3]: Leaving directory `/home/alaisi/NetworkManager/src/vpn-manager'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alaisi/NetworkManager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alaisi/NetworkManager'
make: *** [all] Error 2
alaisi@ubuntu:~/NetworkManager$ 
```
And when compiling from stable release:
```
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I../src/named-manager -I../src/vpn-manager -I../src/dhcp-manager -I../utils -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_VERSION_MAJOR=0 -DDBUS_VERSION_MINOR=36 -DDBUS_VERSION_MICRO=2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DDBUS_API_SUBJECT_TO_CHANGE -I/usr/include/hal -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include    -DDBUS_API_SUBJECT_TO_CHANGE -DG_DISABLE_DEPRECATED -DBINDIR=\"/usr/bin\" -DDATADIR=\"/usr/share\" -DSYSCONFDIR=\"/usr/etc\" -DARP_DEBUG    -g -O2 -MT NetworkManager-NetworkManagerDevice.o -MD -MP -MF ".deps/NetworkManager-NetworkManagerDevice.Tpo" \
  -c -o NetworkManager-NetworkManagerDevice.o `test -f 'NetworkManagerDevice.c' || echo './'`NetworkManagerDevice.c; \
then mv -f ".deps/NetworkManager-NetworkManagerDevice.Tpo" ".deps/NetworkManager-NetworkManagerDevice.Po"; \
else rm -f ".deps/NetworkManager-NetworkManagerDevice.Tpo"; exit 1; \
fi
NetworkManagerDevice.c: In function &#8216;process_scan_results&#8217;:
NetworkManagerDevice.c:4571: error: &#8216;IW_EV_POINT_OFF&#8217; undeclared (first use in this function)
NetworkManagerDevice.c:4571: error: (Each undeclared identifier is reported only once
NetworkManagerDevice.c:4571: error: for each function it appears in.)
NetworkManagerDevice.c:4683: warning: pointer targets in passing argument 2 of &#8216;nm_ap_set_wpa_ie&#8217; differ in signedness
NetworkManagerDevice.c:4686: warning: pointer targets in passing argument 2 of &#8216;nm_ap_set_rsn_ie&#8217; differ in signedness
NetworkManagerDevice.c:4713: warning: pointer targets in passing argument 2 of &#8216;hexstr2bin&#8217; differ in signedness
NetworkManagerDevice.c:4715: warning: pointer targets in passing argument 2 of &#8216;nm_ap_set_wpa_ie&#8217; differ in signedness
NetworkManagerDevice.c:4717: warning: pointer targets in passing argument 2 of &#8216;nm_ap_set_rsn_ie&#8217; differ in signedness
make[3]: *** [NetworkManager-NetworkManagerDevice.o] Error 1
make[3]: Leaving directory `/home/alaisi/NetworkManager-0.5.1/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/alaisi/NetworkManager-0.5.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/alaisi/NetworkManager-0.5.1'
make: *** [all] Error 2
alaisi@ubuntu:~/NetworkManager-0.5.1$

```
So no NW for me at all. :( Any ideas what could help?

---

### Post by Jeff250 on 2006-01-29
(Edit: For those having trouble compiling from CVS: ) By default it is set up to treat compiler warnings as errors, but unfortunately there are known compiler warnings in the current CVS code.  This isn't a problem, but what you have to do is edit the configure.in file that comes with NM and find and delete the instance of '-Werror' (without quotes) in the file.  Save it, and then re-run ./autogen.sh .  It should compile after that.

---

### Post by kaamos on 2006-01-30
Thanks Jeff250! Got in compiled by removing -Werror and commenting out line 3092 (custom += IW_EV_POINT_OFF;) in nm-device-802-11-wireless.c

---

### Post by bugmenot on 2006-01-31
It works!!

EDIT: with ipw2100 (patched kernel module for WEXT=18 ); patched wpa_supplicant and nm-device-802-11-wireless.c (for AP_SCAN 2) and removed -Werror in the configure script. To start the daemon and the applet together I had to loosen the restrictions in /etc/dbus/system.d as well.

---

### Post by Lambert on 2006-01-31
This is good information, anybody consider writing a step by step howto?

---

### Post by Jeff250 on 2006-02-01
I'm up to the challenge.  I'll try to write one up tonight.

---

### Post by aseem_mal on 2006-02-03
[QUOTE=Jeff250]I'm up to the challenge.  I'll try to write one up tonight.[/QUOTE]


Hi Jeff250, Not to rush you, but I am one of those people who are actually anxiously waiting for you to write it up. Again, no rush. This is just FYI. ;) 

Keep up the great work you do for the community!!

---

### Post by Jeff250 on 2006-02-04
I submitted the HOWTO to the customization forum a couple of days ago.  It requires moderation approval before the thread will appear.  I don't know how long it normally takes for this to happen either, or if the thread were somehow lost, or if it were for some reason not approved.  In the meantime, I guess I can post it here though!

Edit:  The guide is now up in the HOWTO section.  It can be found here:
[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

---

### Post by chefmac on 2006-02-05
Hello Jeff250,

I am trying your howto to get my laptop on my wireless router and I have run into a problem.  Maybe I shouldn't have gone down this path because I am a noob but I have been pulling my hair out for the last couple of days trying to get back on my network.  My laptop was worked great using WEP on my old router which blew up recently.  Eventhough I haven't changed anything on my laptop it will not create a new WEP connection on my new router for some reason.  My windows laptop connects fine.  I would much rather use WPA so that is why I am here.

Anyway... my problem is when I run **make** when *Updating the ieee80211 subsystem*.  The only change I have made to your instructions is I installed **linux-headers-386** becuase of my laptop (Dell Latitude D500).

Here is what I get...

Checking in /lib/modules/2.6.12-10-386/build/ for ieee80211 components...
make -C /lib/modules/2.6.12-10-386/build M=/home/chefmac/wpa/ieee80211-1.1.9 MODVERDIR=/home/chefmac/wpa/ieee80211-1.1.9 modules
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-10-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/chefmac/wpa/ieee80211-1.1.9/ieee80211_module.o
/bin/sh: gcc-3.4: command not found
make[2]: *** [/home/chefmac/wpa/ieee80211-1.1.9/ieee80211_module.o] Error 127
make[1]: *** [_module_/home/chefmac/wpa/ieee80211-1.1.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [modules] Error 2

Any help is appreciated.

---

### Post by Jeff250 on 2006-02-05
It looks like that it requires gcc-3.4 to compile.

```
sudo apt-get install gcc-3.4
```
... should do the trick!  I'm going to update the guide to include that.  Thanks for the feedback.  I'm also moving it to the following thread too, now that it's been approved:
[http://www.ubuntuforums.org/showthread.php?t=125150](http://www.ubuntuforums.org/showthread.php?t=125150)

P.S. I also updated it to add the line:
```
sudo rm -rf /lib/modules/$(uname -r)/kernel/net/ieee80211
```
to the ieee8021 installation instructions.  I still don't know if it's necessary, but it cleans out the old ieee80211 modules.  It's not related to the problem that you were having, but you might want to do that too.

---

### Post by chefmac on 2006-02-05
Thanks for the reply.  I have made it through your howto and I re-updated the ieeee80211 module using your additional line.  Everything seemed to have gone well.  I have rebooted and my wireless card (eth0) is no longer listed under Network Settings.  I don't know what to do.

Can you help me?

---

### Post by Jeff250 on 2006-02-05
Are you using Breezy or Dapper?  Which IPW are you using--2100, 2200, or 2915?

Also, output the results of the following commands:
lsmod | grep ieee80211
lsmod | grep ipw
iwconfig --version
(The " | " is the pipe symbol on the keyboard.)

---

### Post by chefmac on 2006-02-05
Breezy, ipw2100

lsmod | grep ieee80211
ieee80211              27012  0
ieee80211_crypt         5636  1 ieee80211

lsmod | grep ipw
*nothing*

iwconfig --version
iwconfig  Wireless-Tools version 28
          Compatible with Wireless Extension v11 to v18.

Kernel    Currently compiled with Wireless Extension v17.

---

### Post by chefmac on 2006-02-05
Been searching through the forums for any ideas.  If I run

*dmesg | grep ipw*

I get this.  Might be a clue...

[4294698.033000] ipw2100: disagrees about version of symbol ieee80211_get_crypto_ops
[4294698.033000] ipw2100: Unknown symbol ieee80211_get_crypto_ops
[4294698.033000] ipw2100: disagrees about version of symbol ieee80211_wx_set_encode
[4294698.033000] ipw2100: Unknown symbol ieee80211_wx_set_encode
[4294698.033000] ipw2100: disagrees about version of symbol ieee80211_wx_get_encode
[4294698.033000] ipw2100: Unknown symbol ieee80211_wx_get_encode
[4294698.033000] ipw2100: disagrees about version of symbol ieee80211_txb_free
[4294698.033000] ipw2100: Unknown symbol ieee80211_txb_free
[4294698.034000] ipw2100: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4294698.034000] ipw2100: Unknown symbol ieee80211_crypt_delayed_deinit
[4294698.034000] ipw2100: disagrees about version of symbol ieee80211_wx_get_scan
[4294698.034000] ipw2100: Unknown symbol ieee80211_wx_get_scan
[4294698.034000] ipw2100: Unknown symbol ieee80211_set_geo
[4294698.034000] ipw2100: disagrees about version of symbol ieee80211_rx
[4294698.034000] ipw2100: Unknown symbol ieee80211_rx
[4294698.035000] ipw2100: disagrees about version of symbol ieee80211_rx_mgt
[4294698.035000] ipw2100: Unknown symbol ieee80211_rx_mgt

---

### Post by Jeff250 on 2006-02-05
Hmm, I'm currently playing around with a Breezy live CD and am running into the same problem.  This might have to do with the fact that the Breezy kernel comes with Wireless Extensions v17, but the latest IPW drivers require v18.  I'm going to play around with it some more and see if older drivers will work.

---

### Post by Jeff250 on 2006-02-05
Older drivers *will* work in general, but I'm now going to see if I can still get them to work with NetworkManager's WPA.  I'll tell you the entire scoop once I'm finished.

---

### Post by Jeff250 on 2006-02-05
Nope, *expletive*, I think it boils down to again Breezy's kernel again not supporting a high enough version of Wireless Extensions or just not being able to use new enough drivers.  I can get everything set up, patched, etc., except NetworkManager still reports that my hardware won't support the network that I'm trying to connect to, and WPA and WPA2 aren't available in the drop-down choices either.

Well, I definitely appreciate you being around for the ride. :D  To get back to your old configuration, this should work:
Go into both your extracted ieee80211 directory and your ipw directory and in both of them type "sudo make uninstall".  After that, run:
```
sudo apt-get --reinstall install linux-386 linux-headers-386
```
Reboot, and then everything should be returned to normal.  You should also unlock network-manager from Synaptic, and even uninstall it if you're not going to be using it.

I'm going to remove anything that suggests that this might work on Breezy from the guide.

The guide will always be there when you upgrade to Dapper. :D

---

### Post by chefmac on 2006-02-06
[QUOTE=Jeff250]Well, I definitely appreciate you being around for the ride. [/QUOTE]

Well... I am still hanging on by a thread. :) 

I was explaining the situation to a co-worker of mine and he helped me to upgrade the kernel to version 2.6.15.  The kernel is up and running and the latest versions of ieee80211 and ipw2100 are working.  My wireless card is back!  Now...

When I try and install wpasupplicant from cvs and run *make* i get...

 undefined reference to `wpa_driver_ipw_ops'
collect2: ld returned 1 exit status
make: *** [wpa_supplicant] Error 1

Any ideas?

---

### Post by Jeff250 on 2006-02-06
I'm going to go off on a wild guess and say that this is happening because you originally compiled wpa_supplicant when the "CONFIG_DRIVER_IPW=y" line was uncommented in the ".config" file and now it is commented (this happened if you re-copied "defconfig" over ".config").  Since the support for IPW was already compiled but now it's commented, the linker that puts all of the object files together is now confused because it doesn't know what to do.  A simple way to remedy this is a "make clean" but we should probably take an extra step since you're using Breezy and add the IPW driver support back in.

I'm not sure if it's even still necessary since you have the new kernel, but let's be safe and uncomment CONFIG_DRIVER_IPW=y from the ".config" file again (can't hurt).
Then type:
```
make clean
make
sudo make install
```

---

### Post by chefmac on 2006-02-07
That was a good guess because it was spot on.  I think I am almost there.  I am now trying to compile NetworkManager.   When I run **make** I get this error message:

In file included from NetworkManagerMain.h:28,
                 from NetworkManagerAPList.h:27,
                 from nm-device-802-11-wireless.c:36:
/usr/include/hal/libhal.h:295: warning: declaration of &#8216;index&#8217; shadows a global declaration
/usr/include/string.h:304: warning: shadowed declaration is here
nm-device-802-11-wireless.c: In function &#8216;process_scan_results&#8217;:
nm-device-802-11-wireless.c:2988: error: &#8216;IW_EV_POINT_OFF&#8217; undeclared (first use  in this function)
nm-device-802-11-wireless.c:2988: error: (Each undeclared identifier is reported  only once
nm-device-802-11-wireless.c:2988: error: for each function it appears in.)
make[3]: *** [NetworkManager-nm-device-802-11-wireless.o] Error 1
make[3]: Leaving directory `/home/chefmac/wpa/NetworkManager/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chefmac/wpa/NetworkManager/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chefmac/wpa/NetworkManager'
make: *** [all] Error 2

I appreciate any help.  Sorry to keep you occupied.

---

### Post by Jeff250 on 2006-02-07
Ah, I ran into that problem using the Breezy Live CD.

You'll need to upgrade your Wireless Tools too (Dapper already comes with this version):
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.28.pre13.tar.gz](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/wireless_tools.28.pre13.tar.gz)

At the console, just "tar -zxvf" it, enter the directory that it creates, and then "make" "sudo make install".  Should do the trick.

---

### Post by chefmac on 2006-02-08
Jeff250 you are a rock star!  I am now wireless on my WPA network.  The only minor issue I have is when I run *nm-applet* I get this error:

 dbus_bus_acquire_service() says: 'Connection ":1.19" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

If I run it using *sudo* then it runs fine.  I made the changes to nm-applet.conf file as you suggested but I still get the error.  I also made sure to copy the file to /etc/dbus-1/system.d/.  Any ideas?

Other than that it is great.  I have had a frustrating week using Linux because of my wireless problems and some PHP/MySQL issues.  I am thinking that the Dapper release will resolve most of those issues.

One question... if I install the Dapper release at a later time will I have to go through your HOWTO again?

Thanks for all of your help and if you are ever in London I will buy you a pint.

**Update:** Nevermind about the error.  I needed to add the policy block to /etc/dbus-1/system.d/NetworkManager.conf also.  No problems now.

---

### Post by Jeff250 on 2006-02-09
I'll add that to the guide in case anyone else runs into that problem.

The only thing you should need to do when you upgrade to Dapper is reinstall ieee80211 and the ipw drivers, but you'll need to do this for any kernel upgrade, including any regular update over Synaptic.

---

