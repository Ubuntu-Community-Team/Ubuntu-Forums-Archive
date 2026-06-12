---
title: "Nvidia Geforce 7200 configuration"
date: 2014-04-19
forum: Multimedia Software
---

### Post by frank52 on 2014-04-19
hello,

i started w/ ubuntu version 9 in 2009 and really hated to upgrade this OS, but had to due to withdrawal of support.  version 9 was nice!

i went to 12.04 and really didn't like all the 'smoke' between me and the desktop and the OS' sluggishness.  the smoke is called Unity. 

things went along ok until a change was made to the nvidia configuration utility and the configuration for my samsung 943 monitor did not work with the geforce video card.  after a bit of searching for a proper configuration i had to remove the video card and fall back to using the onboard video with the monitor.  it did configure to the 1440x900 resolution with the onboard video.

the problem is i don't like being left in the dark!

after reading a few posts 'out there' it is obvious that configuration is a 'common problem' with nvidia, monitors, video cards, and linux.

i'd really like to find a definitive authority that explains the interrelation between xorg.conf, any other config files, nvidia configuration, and anything else in the 'video configuration chain' and how i can get this card/monitor problem resolved so i can use the 1gb video memory in this card instead of sharing ram.  i have gathered so many bits and pieces on this that i'm dizzy!

can someone help me regain my balance?

---

### Post by oldos2er on 2014-04-19
Which Nvidia card?

Thread moved to Multimedia & Video.

---

### Post by frank52 on 2014-04-19
thanks for the reply!

the card is labeled as an ASUS c691pi chipset which shows to be an ASUS en210.  ubuntu shows it to be a geforce 7200 i think?  it is not in the computer right now.  the computer is running using the onboard chipset.

---

### Post by oldfred on 2014-04-19
I just installed 14.04 and nVidia driver.

I have to boot installer with nomodeset, and boot first time after install with nomodeset until I install nVidia driver from system settings or command line.
You have to boot with nVidia card/chip enabled or it will not offer to install nVidia driver because you do not need it.

I have not edited xorg for so long I have forgotten how. 
But if your monitor is not reporting its sizes correctly to the nVidia driver you may have to manually update something.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
      
 [SOLVED] Drivers for nVidia 9500GT
[http://ubuntuforums.org/showthread.php?t=2215070](http://ubuntuforums.org/showthread.php?t=2215070)

My monitor is 4:3 so I prefer the older gnome2 top panel & menus, so I install Ubuntu but convert to fallback/flashback which is the old menu system (almost).

 12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

       
 gnome3 classic
New gnome3.8 flashback
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)

 Kansasnoob on flashback/fallback in Saucy, Quantal and Raring
[http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225](http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225)

---

### Post by frank52 on 2014-04-19
thank you for the reply.

i have edited the xorg.conf file several times yesterday & today.  the last few the system would not boot, so i had to go to command line as root, enable r/w on the file system and delete the xorg.conf file so that the system would boot.  the syncmaster 943 monitor has logged quite a few complaints with linux users.  apparently it is not plug and play detectable by nvidia/linux in conjunction with this card.

some have reported that using a digital cable resolved the problem.  this is not an option.  the monitor serves n computers on a kvm switch, so a vga cable is used.

the problem of course is that i am unable to configure the svga landscape resolution of this monitor to 1440x900 using the asus video card.  with the xorg.conf file absent, the system boots, but the nvidia x server settings utility won't properly configure it to 1440x900.

and i don't know why the monitor does work properly (1440x900) with the onboard chipset.  i seem to recall that i edited a configuration file elsewhere in the system that perhaps loads a modeline command to set it to the 1440x900.  but i have not located this file.

does any of this make sense?

---

### Post by oldfred on 2014-04-19
I think others have posted issues with KVM switches.
Can you connect directly just for the install?

I stopped using VGA cables back in 2006, so not sure anymore about those issues. May contribute to why it does not report correctly.

Grub also has some video settings, but they are just for grub. 
And with the Intel chip some have to add a boot parameter for the exact size, but I think that may confuse nVidia then?

 From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


I think this is only Intel. instead of nomodeset:
 Force Intel Video mode as boot parameter in grub menu - Must change to your screen size, not 1280x1024
video=1280x1024-24@60

---

### Post by frank52 on 2014-04-19
fyi, this is a ubuntu dedicated computer - not dual boot.

i have used a kvm switch with my computers for years without issue.  yes, i can direct connect for configuration.

video is NOT set in grub.  all video is commented.  don't recall where i set it.  seemed to me it was a .conf file in the user section, but i can't find it.  there's no reason this monitor will configure properly with the onboard and not with the asus card, so i believe this command 'lingers'.

to narrow this, where would i put a command in a boot configuration file to make a permanent drive mapping?  for example - smb://192.168.1.1/usb_storage/

some have reported that nomodeset causes blue screen.

---

### Post by frank52 on 2014-04-19
found a link to a page concerning persistent xrandr commands.  this triggered a memory.  anyway the following is written in the ~/.xprofile 
          
                                            . . . . . . . . . . . . . . . . . . . . .


xrandr --newmode "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync


xrandr --addmode VGA1 1440x900_60.00

---

### Post by oldfred on 2014-04-19
I do not use Samba and only occassionly use NFS.

[https://wiki.archlinux.org/index.php/Samba#Add_Share_to_.2Fetc.2Ffstab](https://wiki.archlinux.org/index.php/Samba#Add_Share_to_.2Fetc.2Ffstab)
       [URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab

[/URL]
 [https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

[URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by frank52 on 2014-04-19
removing kvm from monitor path - no change.  removing all nvidia drivers w/ reinstall - no change.

video card identified as geforce 8400 gs?

---

### Post by oldfred on 2014-04-20
Should just be the same as the link above on a user with a 9500GT. 
I have a 9600GT and have used both command line & system gui to install nVidia drivers. 

Does you 8400 support that setting?

---

### Post by frank52 on 2014-04-20
the problem is that it is NOT an 8400!  it is an asus en10?

i am searching for any xorg.conf in the file system that might be 'the' problem.  will give the 9500gt a shot.

one note - i'd rather run 2d than 3d.  when i connect the monitor to the asus card, the desktop switches to the 3d mode.  the native chipset will only support 2d.  this is the primary reason i liked version 9 more than version 12.  this is an internet/www computer only, not 3d gaming.

---

### Post by frank52 on 2014-04-20
i followed the 9500 approach and purged the system.  there were quite a few references to nvidia.  nvidia still identifies the asus en210 as a geforce 8400?  i did not follow the p2 (#11) step 3 code since it looked like the computer might be unusable.  i did follow step 4.

i then modified the xorg.conf according to [http://ubuntuforums.org/showthread.php?t=280683](http://ubuntuforums.org/showthread.php?t=280683) #5 w/ the modeline swap noted later.  i added the Option "ModeValidation" "NoEdidDFPMaxSizeCheck" as recommended.

the system boots into a svga setting without the landscape (1024x768 @60hz).  1440x900 @60hz desired.  70hz best.

closer, but still dizzy.

---

### Post by frank52 on 2014-04-20
after quite some 'quality' and 'fun' time on this exhausting exercise, it is clear there was/is an edid problem and there is finally a resolution based on [this]("http://askubuntu.com/questions/188060/force-video-mode-without-edid-information") thread.  note the monitor works at 1440x900@60hz through the kvm switch.  it sure will be nice when linux/nvidia achieve 'plug n play' on these video card/monitor setups!

these statements are the key.

                              .                .                .               .

    Option         "UseEDIDFreqs"   "False"
    Option         "UseEDIDDpi"     "False"
    Option         "IgnoreEDID"     "True"
    Option         "ModeValidation" "NoVesaModes,NoXServerModes,NoEDIDModes"
    Option         "UseEDID" "FALSE"


.                .                .               .

now if the error messages at boot time would disappear, i'd be extatic!


none of the selected modes were compatible with the possible modes:

Trying modes for CRTC 585
CRTC 585: trying mode 800x600@60Hz with output at 1024x768@60Hz (pass 0)
CRTC 585: trying mode 1440x900@70Hz with output at 1024x768@60Hz (pass 0)
CRTC 585: trying mode 1440x900@60Hz with output at 1024x768@60Hz (pass 0)
CRTC 585: trying mode 800x600@60Hz with output at 1024x768@60Hz (pass 1)
CRTC 585: trying mode 1440x900@70Hz with output at 1024x768@60Hz (pass 1)
CRTC 585: trying mode 1440x900@60Hz with output at 1024x768@60Hz (pass 1)
Trying modes for CRTC 586
CRTC 586: trying mode 800x600@60Hz with output at 1024x768@60Hz (pass 0)
CRTC 586: trying mode 1440x900@70Hz with output at 1024x768@60Hz (pass 0)
CRTC 586: trying mode 1440x900@60Hz with output at 1024x768@60Hz (pass 0)
CRTC 586: trying mode 800x600@60Hz with output at 1024x768@60Hz (pass 1)
CRTC 586: trying mode 1440x900@70Hz with output at 1024x768@60Hz (pass 1)
CRTC 586: trying mode 1440x900@60Hz with output at 1024x768@60Hz (pass 1)

---

### Post by oldfred on 2014-04-20
Video cards are identified by the internal chip set used, less by the brand name that made it. 

If monitor is not giving EDID or correct info then you do have to manually overide settings.

In the old days some settings would damage monitors so it was tried to be conservative on default modes. The newer EDID info greatly simplified the settings issues when it works.

---

### Post by frank52 on 2014-04-20
the syncmaster shows up a lot in linux incompatibility issues.  wish i'd never bought it.  but at least it works now with the vid card.

a simple analog/digital mode setting in the device section would be a better approach.  i suspect that the monitor is running in analog mode since the cabling is vga as opposed to digital.

---

### Post by frank52 on 2014-04-20
thanks for the assistance old fred.

---

