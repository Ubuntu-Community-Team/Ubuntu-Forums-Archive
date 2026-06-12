---
title: "kppp launch problems"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by vic622 on 2009-06-06
Linux Newbie here, first post  & I'm not sure how to resolve this ...

I have an Acer Aspire One & I'm trying to use a Novatel U727 USB modem in Ubuntu 9.04 (kernel 2.26.1).
I had it running last weekend using kppp, however something happened and when I would start it, it was giving me an error msg saying that there was another instance already running. 

I thought I had somehow corrupted the kpp application, so I removed it and reinstalled it. 
When I open the application, I get an error msg:

kppp can not create or read from /home/vic/.kde/share/apps/kppp/kppp/pid

I opened kppp using gksudo and the GUI opened properly - I didn't see the above error.
When I went to configure a new account, this is what I see in the terminal window:

vic@mini-mobile:~$ gksudo kppp
kdeinit4: preparing to launch /usr/lib/kde4/libexec/klauncher
. launching kdeinit
kdeinit4: preparing to launch /usr/bin/kded4
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kbuildsycoca4(4073) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-hcidump.xml" 
kbuildsycoca4(4073) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-pem-key.xml" 
kbuildsycoca4(4073) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/application/x-ssh-key.xml" 
kbuildsycoca4(4073) KBuildMimeTypeFactory::createEntry: Missing <comment> field in  "/usr/share/mime/audio/x-sbc.xml" 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_tunnel.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/colorfire.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/lattice.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/skyrocket.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/solarwinds.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/cyclone.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hyperspace.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/fieldlines.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/spirographx.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/hufo_smoke.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flocks.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/busyspheres.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/matrixview.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/sundancer2.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/biof.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/helios.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/flux.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/plasma.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Actions in "System/ScreenSavers/euphoria.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/winff.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/speedcrunch.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/gcalctool.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(4073) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/openoffice.org-startcenter.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
kdeinit4: preparing to launch /usr/lib/kde4/libexec/kconf_update

It hangs here at the kconf_update.
The GUI is different than when I run it without the gksudo, but it still hangs.
I can see that there are error msg's, but I don't know what they mean & how to resolve them.

Help!
Vic

---

### Post by vic622 on 2009-06-06
Okay, so I opened a terminal and ran:
gksudo "kppp"
I was able to set up a new account & modem profile and launch the dialer, connect to the modem and to the network - I'm sending this from the netbook, now.

Unfortunately, I have to keep the terminal window open until I finish this session - I can live  with that, at least I have a work around.

I still don't know what is the underlying problem & why I need to run this from root., now, when it wasn't necessary, before?

Also, why all the error msg's in my previous post?

Still confused, but connected,
Vic

---

