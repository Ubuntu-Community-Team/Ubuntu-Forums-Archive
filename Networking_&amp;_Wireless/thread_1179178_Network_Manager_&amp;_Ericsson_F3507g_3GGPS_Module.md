---
title: "Network Manager &amp; Ericsson F3507g 3G/GPS Module"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by Master One on 2009-06-05
I am playing with the idea of buying a netbook, which has the mentioned Ericsson F3507g module embedded, that is a combination of UMTS/3G network card and GPS.

I already found out, that this module is supported, and both parts can be used with Linux, but there were problems with Network Manager, which seem to have been solved with Jaunty.

Can anybody tell me please, if that Ericsson F3507g module is now working right out of the box on Jaunty with Network Manager (for WWAN access) and GPS applications (like [tangoGPS](http://www.tangogps.org)), or if there are still some additional steps required, as mentioned on [ThinkWiki](http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module) and various tutorials, suggesting the replacement of NM with WiCD and using UMTSMON for the 3G networking?

---

### Post by torgnyj on 2009-06-22
Yes, the module works with NetworkManager in Ubuntu Jaunty (at least the Dell 5530 variant, but others should too, it's basically just different vendor ids and product ids). The default NetworkManager only uses PPP though but that is probably good enough for most.

From NetworkManager 0.8 (I think) there will be support for modem-manager and there is work ongoing to create a plugin for the Ericsson modules for modem-manager. The advantage is that it will use the cdc ethernet interface which will give you slightly better performance and more options (like network technology selection between 2G/3G etc).

Experimental packages are available that can be used with apt-get or you can build NetworkManager/modem-manager yourself with support for the f3507g/f3607gw modules. Detailed information about both packages and manual compilations can be found at [http://sourceforge.net/apps/mediawiki/mbm](http://sourceforge.net/apps/mediawiki/mbm)

---

### Post by Master One on 2009-06-22
Cool, although I don't have that device yet, and most likely I am not going to fiddle around manually, but just wait for NM 0.8 (or whatever version) with MM support, but still good to know what's going on. :)

---

### Post by aaron@roydhouse.com on 2009-07-08
I have an Ericsson F3507g that I am trying using with NM 0.7 and Jaunty 9.04. It doesn't work very well. 

It use to work sometimes with 9.04 first came out, but there is a bug in the settings editor that prevents you using a blank password, which means I can't actually connect to any 3G service providers - since none of them use non-blank passwords.

When it did work, it would connect 1 of out every 3-4 attempts.

In contract ppp (pon/poff) works very reliably; Except that nothing in Gnome works because NM insist you are off-line if you connect with ppp :-(

Have another look with NM 0.8 comes out, but I can't recommend NM 0.7 for mobile broadband - at least with an Ericsson F3507g.

Aaron.

---

### Post by torgnyj on 2009-07-08
Have a look at [http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page#Alternative_1:_pre-built_packages](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page#Alternative_1:_pre-built_packages)

There are experimental packages available with modem-manager support for the f3507g module that can be used with apt-get.

To use modem-manager you need the cdc_ether module to support your device though and it doesn't out of the box in Jaunty. On [http://sourceforge.net/apps/mediawiki/mbm/](http://sourceforge.net/apps/mediawiki/mbm/) there are information about how to compile a kernel with support for the module. Alternatively you can just hex-edit your existing cdc_ether module to add support for your device. That is a much quicker way and requires no kernel compilation. For details see [http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Hex-editing_cdc_ether](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Hex-editing_cdc_ether)

Edit: Forgot to mention that there is also GPS control sw available at the mbm wiki linked above. Currently it has to be compiled manually though (but no kernel compilation required).

---

### Post by aaron@roydhouse.com on 2009-07-09
Thanks torgnyj that's good information. If I get some spare time I'll try that out.

Hopefully this and NM 0.8 will all come together for 9.10. On the other hand NM 0.7 took two years, so maybe I am being overly optimistic :-)

---

### Post by Siúlóir on 2009-08-25
My Lenovo T400 also has a F3507g mobile broadband module (id 0bdb:1900) which is supported by the kernel out of the box.

There is no problem when I connect using wvdial, however, as most applications using networking rely on NetworkManager (NM), my mail applications as well as Firefox start in offline mode although a connection was established using wvdial.

Now the interesting thing is, when I fire up Jaunty from a live DVD, the modem assistant (MA) (libmba0 0.0.4+bzr66-0ubuntu1) fires up automatically, I can enter my provider's details and NM (0.7.1~rc4.1.cf199a964-0ubuntu2) starts the mobile broadband connection. The connection also appears in the menu when I click on the NM's panel icon.

However, when I boot the installed Jaunty system with exactly the same versions of NM and MA installed, the configured connection does *not* appear in the menu. NM has created a file with the name of the provider as selected with MA in a directory **/etc/NetworkManager/system-connections**. However, this directory does not exist in the live system.

Are there any hidden settings/permission details that inhibit the connection to show up in the menu? Support should be there as was proven by the live system.

ADDENDUM: I just discovered when I turn BT/WWAN/WLAN off and on again using the sliding switch in front of the Notepad, NM tries to connect via UMTS. The question is: why doesn't it after booting?

Cheers

Siúlóir

---

