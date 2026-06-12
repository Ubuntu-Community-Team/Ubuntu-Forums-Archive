---
title: "Ubuntu 10.04 - vdpau not working after restart gdm"
date: 2010-05-27
forum: Multimedia Software
---

### Post by roast_swan on 2010-05-27
Good afternoon.    

I upgraded from Ubuntu 9.10 to 10.04.  
After the upgrade, mplayer no longer play a DVD.  
I put the missing codecs, as described here: [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-10-04-lucid-lynx.html) 
Now DVD worked. 

Also during the upgrade package libvdpau1 was disappeared, I restored it from the default repository.   
Then vdpau worked, but only after a reboot.  
After restarting gdm (select "Log Out" or sudo service gdm stop/start, or Ctrl + Alt + Backspace) an error:    

mplayer -nolirc -vc ffh264vdpau -vo vdpau  Tchaikovsky.The.Nutcracker.2007.720p.BluRay.DTS.LPCM.HDCLUB.mkv 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team

Playing Tchaikovsky.The.Nutcracker.2007.720p.BluRay.DTS.LPCM.HDCLUB.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_DTS) "DTS 5.1 @ 1536 kbps", -aid 0, -alang  eng
[mkv] Track ID 3: audio (A_PCM/INT/LIT) "PCM 2.0 @ 2304 kbps", -aid 1,  -alang eng
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [libdca] DTS decoding with libdca
Stream with high frequencies VQ coding
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio:  192000->192000)
Selected audio codec: [dts] afm: libdca (DTS-libdca)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   1.6 (01.5) of 5299.6 ( 1:28:19.6)  8.9%  

After reboot everything works again.  
I updated libvdpau1 from repository [https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa"), but it did not help, same error.  

Video: nvidia 9600M GT 
Notebook [http://www.acerdirect.co.uk/Acer_Aspire_6935G-944G32Bn_Gemstone_Blue_Laptop_LX.ATQ0X.038/version.asp#top](http://www.acerdirect.co.uk/Acer_Aspire_6935G-944G32Bn_Gemstone_Blue_Laptop_LX.ATQ0X.038/version.asp#top)
Driver set the default, 195.36.15-0ubuntu3, from the standard repositories. 
In Karmic was 185, everything worked.  

Share advice, pls.  

I noticed this feature, I do not know whether it is connected with subj: 
Immediately after loading the gdm starts with the seventh console, ie when you exit the virtual console by Ctrl + Alt + F2 again to hit Ctrl + Alt + F7. 
After you restart gdm is in the eighth console, Ctrl + Alt + F8. 
If I run a guest session, it starts with the ninth console. 
Further, I have not tried. So it should be? 
In the karmic like always with the seventh started.  

When booting too strange things happen. 
Ubuntu Karmic I installed with Alternate CD to an encrypted LVM. 
I booting in text mode, ie without "quiet splash". 
Booting reached requiring a password, when entering the password does not display an asterisk, after entering the password then continue normally. 
After upgrading to Lucid booting lines are shown as a twisted, ladder when entering the password it displays asterisks and when I enter each character again displays prompt. 
I did not like, and I again put the "quiet splash".

---

### Post by pmahapatra04 on 2010-05-28
I confirm this. I've the exact same problem.

---

### Post by roast_swan on 2012-01-06
The problem resolved itself after a system upgrade.
 Thank you all.

---

