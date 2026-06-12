---
title: "DVB aka linuxTV AVerMedia (again) or C&amp;E fix"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by popper on 2006-08-17
as per the my post elsewere in the old Ubuntu 5.10 [http://www.ubuntuforums.org/showthread.php?t=183297&page=5](http://www.ubuntuforums.org/showthread.php?t=183297&page=5) 
Re: HELP - Freecom USB DVB Stick thread

i reproduce my post in this better place, in the hope old and new readers can use it to get their non working Yuan/Yakomo etc DVB-T cards going and perhaps even more, if you add your success and fix to this new general thread.

with many thanks to jochen over on the linux-dvb mailing list, i have now been able to get my DVB2GO Mini Yuan usb card to function in the x86 606 unbuntu, if your card reports " Bus 004 Device 002: ID 14aa:0220 AVerMedia (again) or C&E" when you cold plug it in and do an lsusb , you might be able to get yours working too. 

"
I finally got it working on my kubuntu machine! It seems like that my stick 
has a different USB cold ID, than older/other versions with this chip.

Here is how I did it:
I edited linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h
changed USB_PID_WT220U_COLD from 0x0222 to 0x0220
and everything worked fine.

Although this was just a hack, I think a clean version should be integrated 
into the kernel module. Should I send a patch to this list or can you tell 
me, where I shall send it to?

Best Regards,

jochen "

essentially , in my case after makeing that change from 0x0222 to 0x0220 and re-compiling any of the snapshots or hg, my card can now try and load a firmware in my case dmesg reports its looking for "downloading firmware from file 'dvb-usb-wt220u-02.fw'", your card might ask for another firmware and in that case just place that firmware in the /lib/firmware/$(uname -r)/ dir as per the first post.

also ill remind you that since that OP the dir for the refered firmware has moved to the dvb-usb sub dir
[http://thadathil.net:8000/dvb/fw/dvb-usb/](http://thadathil.net:8000/dvb/fw/dvb-usb/)

check the [http://thadathil.net:8000/dvb/fw/](http://thadathil.net:8000/dvb/fw/) or linuxtv firmware dirs [http://linuxtv.org/downloads/firmware/](http://linuxtv.org/downloads/firmware/) for your dmesg asked for firmware and you should be set.

if for any reason when you plug in your usb DVB-T card it reports yours as anything other than " Bus 004 Device 002: ID 14aa:0220 AVerMedia (again) or C&E" then change the coresponding cold boot line in that hg made home v4l-dvb linux/drivers/media/dvb/dvb-usb/dvb-usb-ids.h file inthe hg dir to your reported No. then see if dmesg will then ask for the right firmware for your card etc.

people that already have a card that report 222 on cold boot dont need to change anything currently, but it seems that the 222 entry is a long standing typo because there are far more products that report 220 on cold pluging.

it seems any reported "AVerMedia (again) or C&E" card will first use
[http://thadathil.net:8000/dvb/fw/dvb...-dtt200u-01.fw](http://thadathil.net:8000/dvb/fw/dvb...-dtt200u-01.fw)
firmware to then load the real (in my case 'dvb-usb-wt220u-02.fw') firmware for your card that 
dmesg will try and load afterwards so you seem to need both firmwares in the /firmware dir to have it work.

i hope this helps some readers that have given up trying to get their reported " Bus 004 Device 002: ID 14aa:0220 AVerMedia (again) or C&E" cards working and usable.....

remember to check that dvb-usb-ids.h file for your reported cold boot card and make your changes there , then recompile,

i didnt bother to mess about with make config stage and just used make , then make install so as to just make all the cards to simplyfy the options, try it if your not bothered about the small extra space it takes up on your drive.


PS.
is there a simple GUI app/script (rebol view?)thats in the unbuntu repositry that can convert my fully tuned UK winterhill kaffeine /home/ubuntu/.kde/share/apps/kaffeine/channels.dvb file to something vlc can use so i can try and use vlc to multicast my dvb selections over the network as i do now in windows please?.

---

### Post by donalduk on 2006-08-17
Hello,

I followed your old thread and have been tearing my hair out trying to get my dvb-usb to work.  I am using Kubuntu 6.06 and had the Freecom DVB-USB stick working but had to reinstall when my laptop partition table got corrupted.  I went back to get the dvb stick working as I had before, following the same intructions - as in the 5.10 thread opening page.  This time I run into problems when running make in v4l-dvb - 

/home/donald/v4l-dvb/v4l/tvmixer.c:90: error: storage size of 'va' isn't known
/home/donald/v4l-dvb/v4l/tvmixer.c:126: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:126: error: (Each undeclared identifier is reported only once
/home/donald/v4l-dvb/v4l/tvmixer.c:126: error: for each function it appears in.)
/home/donald/v4l-dvb/v4l/tvmixer.c:141: error: 'VIDEO_AUDIO_BASS' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:143: error: 'VIDEO_AUDIO_TREBLE' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:154: error: 'VIDEO_AUDIO_MUTE' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:155: error: 'VIDIOCSAUDIO' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:159: warning: type defaults to 'int' in declaration of '_x'
/home/donald/v4l-dvb/v4l/tvmixer.c:161: warning: type defaults to 'int' in declaration of '_x'
/home/donald/v4l-dvb/v4l/tvmixer.c:161: warning: comparison of distinct pointer types lacks a cast
/home/donald/v4l-dvb/v4l/tvmixer.c:90: warning: unused variable 'va'
/home/donald/v4l-dvb/v4l/tvmixer.c: In function 'tvmixer_clients':
/home/donald/v4l-dvb/v4l/tvmixer.c:297: error: storage size of 'va' isn't known
/home/donald/v4l-dvb/v4l/tvmixer.c:343: error: 'VIDIOCGAUDIO' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:345: error: 'VIDEO_AUDIO_VOLUME' undeclared (first use in this function)
/home/donald/v4l-dvb/v4l/tvmixer.c:297: warning: unused variable 'va'
make[3]: *** [/home/donald/v4l-dvb/v4l/tvmixer.o] Error 1
make[2]: *** [_module_/home/donald/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/donald/v4l-dvb/v4l'
make: *** [all] Error 2


I have firmware loaded as follows - file:///lib/firmware/2.6.15-26-386/dvb-usb-dtt200u-01.fw
file:///lib/firmware/2.6.15-26-386/dvb-usb-wt220u-02.fw
file:///lib/firmware/2.6.15-26-386/dvb-usb-wt220u-zl0353-01.fw

Any help or pointers would be wonderful!  I'm struggling with this.

Donald

---

### Post by popper on 2006-08-19
i seem to remember that a fix for that compile error was added,did you try and re-hg the whole dir again after deleting
the old one, perhaps that might help you successfully compile it.

if not then try grabbing the last snapshot 
wget [http://www.linuxtv.org/downloads/snapshots/v4l-dvb-ChangeLog-20060717](http://www.linuxtv.org/downloads/snapshots/v4l-dvb-ChangeLog-20060717)

wget [http://www.linuxtv.org/downloads/snapshots/v4l-dvb-20060717.tar.gz](http://www.linuxtv.org/downloads/snapshots/v4l-dvb-20060717.tar.gz)

---

