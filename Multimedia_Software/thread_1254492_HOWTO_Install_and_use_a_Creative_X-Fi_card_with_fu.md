---
title: "HOWTO: Install and use a Creative X-Fi card with full 5.1 support"
date: 2009-08-31
forum: Multimedia Software
---

### Post by Lantizia on 2009-08-31
EDIT:

This guide *should* work with these cards... however why you're still using 9.04 is beyond me...
* Creative Sound Blaster X-Fi Elite Pro
* Creative Sound Blaster X-Fi Platinum
* Creative Sound Blaster X-Fi Fatal1ty®
* Creative Sound Blaster X-Fi XtremeGamer
* Creative Sound Blaster X-Fi XtremeMusic

EDIT: NOTE: P.S.: WHATEVER:

DO NOT follow this guide if you are on a later version than 9.04, as this is support is already included

---

Hi,

I installed Ubuntu 9.04 today (EDIT: and Linux Mint 7 a couple of days later)... and I was about to compile the half-baked official Creative X-Fi drivers for my X-Fi Music PCI card... their drivers always have some kind of issue so I checked Wikipedia for any news.  It seems a S.u.S.E. developer has been working with Creative and ALSA, and suffice to say the 1.0.21 release of ALSA that came out a few hours ago has worked great for me with 5.1 support for these X-Fi cards.

I don't think it's going to harm to upgrade ALSA this way, it might be that 9.10 will come with this version in a months time (it currently has 1.0.20 which I haven't tried) and just override the process below anyway.

**_Step One_**
*Upgrade ALSA to version 1.0.21*
Run these commands as root!  To work as root, key in this along with your password...
```
sudo su
```
Then proceed...
```
apt-get -y install build-essential ncurses-dev gettext xmlto linux-headers-`uname -r`
mkdir -p /usr/src/alsa
cd /usr/src/alsa
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2
tar xjf alsa-driver*
tar xjf alsa-lib*
tar xjf alsa-utils*
cd alsa-driver*
./configure
make
make install
cd ../alsa-lib*
./configure
make
make install
ln -s libpanelw.so.5 /usr/lib/libpanelw.so
ln -s libformw.so.5 /usr/lib/libformw.so
ln -s libmenuw.so.5 /usr/lib/libmenuw.so
ln -s libncursesw.so.5 /lib/libncursesw.so
cd ../alsa-utils*
./configure
make
make install
```
**_Step Two_**
*Reboot...*
No really, go reboot... you need to.
**_Step Three_**
*Check preferences...*
[LIST]
[*]Go to your System | Preferences | Sound
[*]Change the default mixer tracks device to 'Creative X-Fi (Alsa mixer)'.
[*]Open Volume Control | Preferences
[*]Tick 'Center/LFE', 'Surround' and 'Side', then unmute each of them.
[/LIST]
**_Step Four_**
*Up mix anything stereo to 5.1...*
If you've got a program that's 5.1 aware then it'll work as it should, however by doing this step anything that plays stereo (like the irritating Ubuntu system sounds) will be up mixed to 5.1 instead of just coming out of the front left and right!
[LIST]
[*]Hit Alt+F2 and run this...
[/LIST]
```
gedit .asoundrc
```
[LIST]
[*]Paste in this stuff below, then save and quit gedit...
[/LIST]
```
pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
```
**_Step Five_**
*Not really a step, I just think 5 steps sound better than 4...*
Remember back in Windows there is that snooty little women who barks all around you in each speaker... she is back!
[LIST]
[*]Hit Alt+F2 and run this...
[/LIST]
```
speaker-test -Dplug:surround51 -c6 -l1 -twav
```
You should hear her come out of each of the 5 speakers, and probably a gagged version of her mumblings out of your sub woofer.

You'll also notice in your Hardware Drivers dialogue box, that it'll say the X-Fi Drivers 1.03 are activated... not sure why it does this - but it does happen as a result of doing this.

Please let me know how you get on... can't promise I'll know what to do when stuff goes wrong for you however!

:popcorn:
Yes that's right popcorn, why? WHY NOT!

NOTE: I am finding that even if I unmute those extra 3 properties in the volume control, they are muted again upon login again - does anyone know a fix for this?

---

### Post by hawks1282 on 2009-08-31
Amazing coincidence, just yesterday I installed Ubuntu to try and begin moving away from Microsoft, and I was up late trying to get my X-Fi card working properly (and not having any success).  Then today I look and see that just ten hours ago, you posted the solution to my problems.  :lolflag:

Everything worked great, except that when I finished the last step there was no sound from the two rear speakers (center, front-right, front-left, and sub all worked).  I went back and fiddled with the controls a bit, and got it working.  The fix that worked for me follows . . . 

Went to "Volume Control->Preferences"
Ticked "Side Playback"
Un-muted "Side"
Ran the "speaker-test -Dplug:surround51 -c6 -l1 -twav" test again and received 5.1 surround goodness for my efforts.  

Thanks very much.

---

### Post by xenogia on 2009-09-01
Thanks [Lantizia]("http://ubuntuforums.org/member.php?u=745784"),

I'm going to check it out probably tomorrow.. wish I could tonight, but thanks for the info.

EDIT:
Just a quick question will this work in conjuction with PulseAudio, or will I have to remove that element for this to work correctly?

---

### Post by algepy on 2009-09-01
that's awesome! really work for me )
thx Lantizia

---

### Post by Lantizia on 2009-09-01
> **hawks1282 said:**
> Went to "Volume Control->Preferences"
Ticked "Side Playback"
Un-muted "Side"

Cool, have updated my post to include this... which card to you have?  Mine is a X-Fi Music card (PCI model not PCI-E).

> **xenogia said:**
> Just a quick question will this work in conjuction with PulseAudio, or will I have to remove that element for this to work correctly?

Don't see why it wouldn't, it's basically just an ALSA upgrade.

---

### Post by crazyone on 2009-09-01
thansk for the guide. works great for me in debian and ubuntu 9.04 both being 64bit

edit: for some reason it wont play sound with bass out of my headset. its a 5.1 headset and the sound card is the xfi xtrememusic pci version. i added the .asoundrc file and also my sound profile is saying that the sourond sound is unpluged. any ideas on this?

---

### Post by Soilworker on 2009-09-01
Thank you very much for writing this guide. This was quite easy to follow and worked flawlessly in Ubuntu 9.04 64bit with a Sound Blaster X-fi XtremeMusic.

---

### Post by hawks1282 on 2009-09-01
My card is a "Sound Blaster X-Fi Titanium Fatal1ty Professional", model: 70SB088600002.  It's a PCI-E card.  Still going strong :D

---

### Post by Lantizia on 2009-09-02
> **crazyone said:**
> thansk for the guide. works great for me in debian and ubuntu 9.04 both being 64bit
Cool, I was using the 64-bit Ubuntu 9.04 when I wrote this... I also frequently use Debian Lenny so it's good to know it works there too, not that there would be any reason it wouldn't.

> **crazyone said:**
> for some reason it wont play sound with bass out of my headset. its a 5.1 headset
No ideas, I don't even know what a 5.1 headset is... presumably one with more than one jack plug.

---

### Post by TRANQU111TY on 2009-09-04
What happens if I'm only using 3.1 because my rear speakers don't work. Do I need to change anything or just leave it as is?

Also I have sound in Youtube but not in movie player. How can I fix this?

---

### Post by TRANQU111TY on 2009-09-05
> **TRANQU111TY said:**
> Also I have sound in Youtube but not in movie player. How can I fix this?

I solved this. I went to System >> Preferences >> Sound. Chose under Devices >> Music and Movies - Sound playback: Creative X-Fi 20K1 Unknown Front/WaveIn (ALSA).

Works fine now.

Although I couldn't get my Skype to work with the X-Fi, I now use my speakers only on the X-Fi and my headphone unit on my on-board sound. It's great because I don't need to unplug and reconnect my leads any more.

---

### Post by Rrasyrogenees on 2009-09-08
i did all that you said Lantizia and i tried the sound test and only get her giving me front left (slight pause) front right... and that is all... i tried what others have said that they did but still get nothing else but those two... if you were here you might look at my computer to see if it is connected properly or something but all looks good to me at the moment.

any suggestions would be appreciated cause i am really trying to get my headset with microphone working so i can use ventrilo for gaming.

i am also using ubuntu 9.04 amd64 with creative x-fi xtreme music... also on a asus m3a78-em board phenom 9950 and 8gb ram

---

### Post by Rrasyrogenees on 2009-09-08
now my vlc won't run... that is my favorite player yet xine works... go figure

---

### Post by Lantizia on 2009-09-08
> **Rrasyrogenees said:**
> only get her giving me front left (slight pause) front right... and that is all

Sounds like you haven't unmuted center, side, and rear.

---

### Post by xenogia on 2009-09-08
Just to note if your using Wine also with the new ALSA drivers to put Sound Acceleration as "Emulation" instead of "Hardware" otherwise you get sound stutters. :)

---

### Post by Lantizia on 2009-09-08
> **xenogia said:**
> Just to note if your using Wine also with the new ALSA drivers to put Sound Acceleration as "Emulation" instead of "Hardware" otherwise you get sound stutters. :)

OMG, I've not tested this but it would explain alot!

Thanks xenogia, will try this when I get home... have been blaming Crossover so far for this!

I take it this is some kind of option in winecfg?

---

### Post by xenogia on 2009-09-08
> **Lantizia said:**
> OMG, I've not tested this but it would explain alot!

Thanks xenogia, will try this when I get home... have been blaming Crossover so far for this!

I take it this is some kind of option in winecfg?

Correct under the Sound Tab, the option is at the bottom of the window.

---

### Post by bjorkiii on 2009-09-09
Is there anyway possible to output 44.1 rather than 96 ? its baffling me:lolflag:

---

### Post by asifraj on 2009-09-10
I followed all the steps as mentioned in the post 1, and the sound works. but its stuttering and a regular beeping sound is added to the sound of the video being played. A little more googling told me that the pulse audio drivers could be the cause. I have removed all the pulse audio drivers and rebooted, but still the problem.

Kernvel v. 2.6.28-15-generic

---

### Post by oneils on 2009-09-23
Wow, awesome post. Thanks very much. This helped me a lot.

Tips for noobies like me, paste each line of code (found in the second text box of step one) one at a time. I actually just cut and paste all the commands and pasted them in the terminal. That does not work. Obviously i have a lot to learn.

Again, great info and thanks.

---

### Post by GeekGirl1 on 2009-09-26
I was having many problems with my configuration. I always had errors of alsamixer reporting "No file", "aplay -l" could not find an audio card, and no sound devices were installed in /etc. Driver compiling was successful, but something was missing. Finally, success!! :) Here is the complete process. Jaunty 9.04, Gnome, 2-channel stereo (the 5.1 channel test in Post #1 works correctly for my Front R/L speakers).

First, do everything in Post #1. If you have problems with sound, then try this. Based on the [Debian X-Fi Wiki]("http://wiki.debian.org/X-Fi") (thank you!) with a few changes. When you run 'su', notice the prompt changes to "#". You are now root. Be careful. You can also put "sudo" in front of each command. Copy the entire line except for the "$" or "#" command prompts.

Install the alsa-base and alsa-utils packages, along with necessary compilation packages:> $ su
# aptitude install alsa-base alsa-utils build-essential linux-headers-$(uname -r)
Unload any currently loaded ALSA drivers:> # alsa unloadIf previously installed, remove the alsa-modules-* package (built from alsa-source) from your system:> # aptitude remove alsa-modules-$(uname -r)Since the script in Post #1 has already downloaded and unpacked the drivers, skip to the driver installation. First, create the sound device directories. Then, configure and compile drivers providing X-Fi device support. Note the different command line than Post #1 and you are still root:> # cd alsa-driver-1.0.21
# snddevices
# ./configure --with-isapnp=no --with-cards=ctxfi,ca0106,hda-intel --with-moddir=/lib/modules/$(uname -r)/updates/alsa
# makeInstall only the kernel modules:> # make install-modulesThe driver should be ready to go. Now, load the ALSA driver (insert into kernel).> # modprobe snd-ctxfiYou should have sound. Run alsamixer to un-mute the channels. Hit "M" on each channel to mute/unmute.> alsamixerLet's make some noise.> aplay /usr/share/sounds/alsa/Noise.wavConfigure Ubuntu to load the mixer settings at boot. From the [ALSA Quick Install wiki](http://alsa.opensrc.org/index.php/Quick_Install) (the filenames have specific meaning). The last line will take you out of root:> # ln -s /etc/init.d/alsasound /etc/rcS.d/S59alsasound
   # ln -s /etc/init.d/alsasound /etc/rc1.d/K15alsasound
   # ln -s /etc/init.d/alsasound /etc/rc6.d/K15alsasound
# exitSave your mixer settings, from the [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449):> sudo alsactl store 0Now, configure Ubuntu to load the drivers at boot.> sudo gedit /etc/modulesAdd the following 2 lines (the first is a comment):> #X-fi
snd-ctxfiConfigure ALSA for your soundcard.> sudo gedit /etc/modprobe.d/alsa-base.confAdd the following lines. Note that I commented out the *alias* and *options* for the snd-hda-intel driver. This may not be totally correct, but it works in my configuration. Refer to the [ALSA Driver Configuration Guide](http://git.alsa-project.org/?p=alsa-kmirror.git;a=blob;f=Documentation/ALSA-Configuration.txt;h=bf24429b7a8f22711ac7a4b9ccce4ad26b50b8bd;hb=15db13e5608030eef093573088a76907a51ca2c7) for the gory details.> #added for alsa driver update
#alias snd-card-0 snd-hda-intel
#options snd-hda-intel model=auto
alias snd-card-0 snd-ctxfiFinally, add your login to the 'audio' group. Follow _Adding the current user to the audio group_ in the [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449).

One additional reference: Ubuntu's [Sound Troubleshooting Guide](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by GeekGirl1 on 2009-09-26
After I got my X-Fi driver up and running, the kernel is complaining about a version mismatch with the snd-ctxfi driver. Perhaps I missed something? Otherwise, I'll just let the warnings remain. Content of /var/log/messages:
>  ctxfi: disagrees about version of symbol snd_ctl_add
 ctxfi: Unknown symbol snd_ctl_add
 ctxfi: disagrees about version of symbol snd_pcm_new
 ctxfi: Unknown symbol snd_pcm_new
 ctxfi: disagrees about version of symbol snd_card_register
 ctxfi: Unknown symbol snd_card_register
 ctxfi: disagrees about version of symbol snd_card_free
 ctxfi: Unknown symbol snd_card_free
 ctxfi: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
 ctxfi: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
 ctxfi: disagrees about version of symbol snd_pcm_hw_constraint_minmax
 ctxfi: Unknown symbol snd_pcm_hw_constraint_minmax
 ctxfi: disagrees about version of symbol snd_ctl_new1
 ctxfi: Unknown symbol snd_ctl_new1
 ctxfi: Unknown symbol snd_card_new
 ctxfi: disagrees about version of symbol snd_pcm_lib_malloc_pages
 ctxfi: Unknown symbol snd_pcm_lib_malloc_pages
 ctxfi: disagrees about version of symbol snd_pcm_lib_ioctl
 ctxfi: Unknown symbol snd_pcm_lib_ioctl
 ctxfi: disagrees about version of symbol snd_pcm_lib_free_pages
 ctxfi: Unknown symbol snd_pcm_lib_free_pages
 ctxfi: disagrees about version of symbol snd_ctl_notify
 ctxfi: Unknown symbol snd_ctl_notify
 ctxfi: disagrees about version of symbol snd_pcm_set_ops
 ctxfi: Unknown symbol snd_pcm_set_ops
 ctxfi: disagrees about version of symbol snd_device_new
 ctxfi: Unknown symbol snd_device_new
 ctxfi: disagrees about version of symbol snd_pcm_hw_constraint_integer
 ctxfi: Unknown symbol snd_pcm_hw_constraint_integer
 ctxfi: disagrees about version of symbol snd_pcm_period_elapsed
 ctxfi: Unknown symbol snd_pcm_period_elapsed

---

### Post by Capt. Blackwood on 2009-09-29
Personally i'd wait until the release of Ubuntu 9.10, then your card's 5.1 capability will run out of the box with no issues, i've tested the alpha personally and i can say...that it works.

---

### Post by GeekGirl1 on 2009-10-02
Yes, it's easier to wait until 9.10. I could have also upgraded the kernel, which has the driver. However, it was a great way for me to really dig in and learn how Linux works. I posted the details so others can learn (or tell me where I went wrong :) ). I'll live with the warnings until 9.10.

---

### Post by dreadnought on 2009-10-11
Many thanks to lantizia for this howto. My X-fi card is working perfectly with kubuntu jaunty updated to kde4.3.2.
I just followed your instructions line by line.
Great work
Cheers
Dave\\:D/

---

### Post by Garyu on 2009-10-12
> **Capt. Blackwood said:**
> Personally i'd wait until the release of Ubuntu 9.10, then your card's 5.1 capability will run out of the box with no issues, i've tested the alpha personally and i can say...that it works.

Does the microphone work now as well? I was almost 100% migrated from windows to Ubuntu a couple of years ago, then I started with MMO gaming. My microphone  wouldn't work with the then very basic X-Fi drivers and there was only crappy stereo sound. I would have lived with the crappy sound if I only had microphone support, but I really need Ventrilo/TeamSpeak for my raids. 

Funny how a simple thing as a microphone can turn into a dealbreaker. But I'm currently running Windows 7 RC that keeps crashing at random occasions, so would love to get back to my stable and secure linux, but would be nice to know if the microphone has been fixed yet? I'd rather crash and have viruses than be gagged.

---

### Post by mjprashanth on 2009-11-11
Wonderful..It just worked like a breeze..I have been working for so long and was unable to get it to work... 

The Linux World is just Amazing

---

### Post by NerdRacer on 2009-11-27
Wow, this sounds almost too good to be true!
 
I had everything, including upgrading my left-over iTunes DRM music to Non-DRM to switch to Ubuntu in mid-october with 9.04........and as expected, the stopping point was my X-Fi Fatality PCIE Card, I used the Optical Out (Passthrough) to my Reciver, and even with headphones on the Analog connections, I could get no sound!
 
But by the sounds of several posts, X-Fi Fatality is a high-chance of working out of the Box now......with Optical Out?

---

### Post by Garyu on 2009-11-28
> **NerdRacer said:**
> But by the sounds of several posts, X-Fi Fatality is a high-chance of working out of the Box now......with Optical Out?

Well, out of the box stereo. To get 5.1 you have to fiddle around a bit, but it's not difficult at all. Just install alsa-mixer and pull a few levers around. 

Optical out... I spoke to a guy at work the other day who said he had opened a stream to get the sound digital through to his reciever. As I understood, he got it to work. But I also assume this requires quite a bit of fiddling around and a lot more advanced fiddling than just pulling a few levers.

---

### Post by jamessimo on 2010-07-30
Hey, i'm a x-fi xtreme card on Ubuntu 10.04, I tried to follow post #1 but when I get to ./configer and make ect in terminal it says no such file or directory. Been trying to get sound all day now! :cry:

---

### Post by Lantizia on 2010-07-30
Hi...

Do NOT - I repeat NOT - follow this guide if you are on 9.10 or 10.04 as it already comes with this built in.

I will edit the first post to reflect this.

---

### Post by jamessimo on 2010-07-30
> **Lantizia said:**
> Hi...

Do NOT - I repeat NOT - follow this guide if you are on 9.10 or 10.04 as it already comes with this built in.

I will edit the first post to reflect this.

If it comes built in why do I have no sound?

---

### Post by Lantizia on 2010-07-30
> **jamessimo said:**
> If it comes built in why do I have no sound?

I have no idea, start a new thread for that.

---

### Post by jamessimo on 2010-08-05
> **Lantizia said:**
> I have no idea, start a new thread for that.
  Hi Lantizia, I have made my own thread for my sound problems here [http://ubuntuforums.org/showthread.php?p=9680939#post9680939](http://ubuntuforums.org/showthread.php?p=9680939#post9680939) 

I still have no sound and would love any input you or anyone else can offer. Really hitting my head against the wall here! Thanks.

---

