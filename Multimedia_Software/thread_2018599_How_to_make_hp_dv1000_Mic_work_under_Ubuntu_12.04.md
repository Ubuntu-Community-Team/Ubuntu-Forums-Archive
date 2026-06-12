---
title: "How to make hp dv1000 Mic work under Ubuntu 12.04"
date: 2012-07-06
forum: Multimedia Software
---

### Post by aimwin on 2012-07-06
**[SIZE="3"]How to make hp dv1000 Mic work under Ubuntu 12.04[/SIZE]**
[B]
You need 
*options snd-hda-intel model=auto enable=yes*
in the last line of 
*sudo gedit /etc/modprobe.d/alsa-base.conf*[/B]

For Newbies, you can go directly to below "***_[SIZE="4"]Tutorial Begin here.[/SIZE]_***"
and those that do not understand the above 2 lines
and those who has other brands and models
please read on.

I made this tutorial from 
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/202049](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/202049) which link to
[http://askubuntu.com/questions/75828/external-microphone-not-working](http://askubuntu.com/questions/75828/external-microphone-not-working)
Thanks actionparsnip (andrew-woodhead666) very much for the Answer.

[B][SIZE="3"]dv1000, ( dv1729tu ) has succesfully working external mic jack.
Confirm with 12.04 fresh installed,[/SIZE][/B]
(after test succesful with 2 partitions of old-"staled" installed 12.04,
I decide to do fresh install to proof the tutorial)

[U][B]10.04 Lts (in another partition of my dv1000) is not working at all,
eventhough using the same procedure.
Mic is still not working under Ubuntu 10.04.

******* If any can get it work please help report it here ************************[/B][/U]
==============================================

[B][I]Please note other brands and models should not use this tutorial as it is,
especially in NO.2 step.
Please look into 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
for more info on this issue.

Each brand of computer and each models need different "codes" to add to the last line,
or it may need to put "#", to disable codes,
in front of certain "lines of codes" to get the microphone or speakers to work.
Or even it may need to do other "ways"[/I][/B]

[COLOR="Red"]Please seach in Google for your specific models if you have problems with these kinds.

When you are face bad luck that Ubuntu will not work out of the box.[/COLOR]

To get help, best one on this Alsa sound issue

[https://answers.launchpad.net/ubuntu/+source/alsa-driver](https://answers.launchpad.net/ubuntu/+source/alsa-driver)
Steps to get help.
1. Register to the launchpad first
2. Login
3. Key in your question in the question box on the left upper conner.
4. give it 1-2 days someone should come in and help.

But [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php) where you are now,
is also very good place to search for previous samples of solutions,
but to get the fastest help it seem to be 
[https://answers.launchpad.net/ubuntu/+source/alsa-driver](https://answers.launchpad.net/ubuntu/+source/alsa-driver)
====================================================================
**links that may help you solve your problems on sound issue for Ubuntu**
[https://answers.launchpad.net/ubuntu/+source/alsa-driver](https://answers.launchpad.net/ubuntu/+source/alsa-driver)
[http://askubuntu.com/questions/75828/external-microphone-not-working](http://askubuntu.com/questions/75828/external-microphone-not-working)
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting#Line_Input.2BAC8-Microphone_Troubleshooting)

====================================================================
***_[SIZE="4"]Tutorial Begin here.[/SIZE]_***

[COLOR="Blue"][U]Before you continue, please test your external Mic first,
prefered dual boot windows on the same machine.
So we know for sure that the sound hardware of the computer and the microphone work 100%.[/U][/COLOR]

[B][B][SIZE="3"]1. [COLOR="Red"]Open Terminal[/COLOR] 
(Click on "Dash Home" just key in T in the pop up search box, you will see Black Terminal icon)

[COLOR="Red"]key in[/COLOR] or [COLOR="Red"]select copy and paste[/COLOR] the following command line, into Terminal and press ENTER[/SIZE][/B] [/B]

[SIZE="3"][COLOR="Red"]sudo gedit /etc/modprobe.d/alsa-base.conf
[/COLOR]
[/SIZE]
Youe will be prompt to put pass word then,
you will have new pop up window with.(I highlighted the last 2 lines in blue)......>


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
.............
..............
(I ommited these lines of codes to shorten the display samples).......
,,,,,,,,,,,,,,,,,,
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
[COLOR="Blue"]# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2[/COLOR]
==============================================

[B][SIZE="3"]2. Sample vedio for this step.

The Youtube "How to fix not working microphone in Ubuntu 10.04"  
[U][B][I]But do not use his full details, 
but use the No.2 step in my tutorial instead for hp dv1000
_And for my Ubuntu 10.04 it did not work at all for my hp dv1000_
and you must do No.4 and No.5 step which are not in vedio,
so the video is just sample how to do step 2 only/I][/B][/U]
[http://www.youtube.com/watch?v=tULmqpe5Yos](http://www.youtube.com/watch?v=tULmqpe5Yos)

just add the following line[/SIZE][/B]

[COLOR="Red"]**[SIZE="2"]options snd-hda-intel model=auto enable=yes[/SIZE]**[/COLOR]

to the last line of the "alsa-base.conf",

so you will have below, take notice of the last line in Red follow the previous last blue lines............>

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
.............
..............
(I ommited these lines of codes to shorten the display samples).......
,,,,,,,,,,,,,,,,,,
[COLOR="Blue"]...............................
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2[/COLOR]
[COLOR="Red"]options snd-hda-intel model=auto enable=yes[/COLOR]
====================================
[COLOR="Red"][SIZE="3"][B]3. Click "Save" on Gedit Menu (Text Editor Menu) 
4. and then REBOOT[/B][/SIZE][/COLOR]
======================================
After reboot.

[B][SIZE="3"]5. go to "System Setting" and then double click on "Sound".

then Click on INPUT. TAB and [COLOR="Red"]"Unmute"[/COLOR] the LINE IN.[/SIZE][/B]

MICROPHONE JACK is for external microphone so it is "LINE IN" as input port.
Microphone will not work if you leave this this LINE IN muted.


(I found it is muted by default, and many other confirm this in many posts in the ubuntuforum.org)
(How ever my "old-staled" installed Ubuntu 12.04, I did not have to unmute the Line IN,
it worked after the reboot, that may due to many experiments to solve the issues earlier)

[B][U]For those who had install Classic Menu for Ubuntu 12.04, 
you have to click the arrow on the right hand side of the "Choice Box" and choose Line IN,
instead of Microphone and Click UNMUTE Line IN.[/U][/B]
(It should show Microphone in the "Choice Box" by defaut.)

NOW click on Sound Recorder , or install Skype and try to record the sound from the external mic.
IT SHOULD WORK.

=======================================
This tutorial is for Ubuntu 12.04 with "hp dv1000"
iF YOU HAVE other models please do "GOOGLE"

---

### Post by neu5eeCh on 2012-07-08
**Holy**... :shock: Thanks for PM'ing me! This is as far as anyone has gotten me in about three years**!**

OK... so... the internal mic works for the first time since installing Linux *anything* on this laptop in what... three... four years? _**:KSThat**_:KS is amazing. I am... almost speechless.

But... I still can't get my mic to work. I use Xubuntu on this laptop, but have Ubuntu (ubuntu-desktop) installed. I haven't tried booting into Unity (for this issue) but am going to, seems like I ought to be able to solve this from the Xubuntu DE. 

Here is where I get tripped up:

> After reboot.

[SIZE=3]5. go to "System Setting" and then double click on "Sound".[/SIZE]I don't have this option under Xubuntu. I have the *pulse audio volume control* dialog box but un-muting the *microphone* _or_ the *line in* options don't get me a working microphone. Am going to log into unity and see if I can fix this.

**UPDATE: **I logged into the Ubuntu/Unity Desktop and the mic worked without having to adjust anything. I logged out. I logged back into the Xubuntu Desktop and everything works. There must be some _Unity_ specific setting involved, but hey! -- behold my **fully** functional _**battle-station**_! [coughs... clears throat...]... er.... laptop. 

You. Are. A. God. :shock:

---

### Post by aimwin on 2012-07-08
> **VTPoet said:**
> **Holy**... :shock: Thanks for PM'ing me! This is as far as anyone has gotten me in about three years**!**........
..............
**UPDATE: **I logged into the Ubuntu/Unity Desktop and the mic worked without having to adjust anything. I logged out. I logged back into the Xubuntu Desktop and everything works. There must be some _Unity_ specific setting involved, but hey! -- behold my **fully** functional _**battle-station**_! [coughs... clears throat...]... er.... laptop. 

You. Are. A. God. :shock:

Very happy to hear that. It took me a few years too, I did stop using dv1000 since I could not get the sound work. But "Ubuntu" burnt my Ausus Note book (I could not find any power software that will spin up my internal fan, and GPU went up to 75 degreeC and burnt in JUNE 2012). And I could not repair it. So I have to use dv1000, once again. So I was forced to find the solution. 
Have to thanks actionparsnip (andrew-woodhead666) for pushing me to the answer.
========> please let me know, when you say ===>"I logged into the Ubuntu/Unity Desktop and the mic worked without having to adjust anything."

Did you put ==>
options snd-hda-intel model=auto enable=yes
in the last line of
sudo gedit /etc/modprobe.d/alsa-base.conf
==> in Ubuntu before your Mic work? 
sorry your statement did not mention if you modify alsa-base.conf or not.

Thank you

---

### Post by neu5eeCh on 2012-07-08
> **aimwin said:**
> 

Did you put ==>
options snd-hda-intel model=auto enable=yes
in the last line of
sudo gedit /etc/modprobe.d/alsa-base.conf 

Yes. I modified alsa-base and rebooted but I still could not get the *external* mic (though the *internal* mic worked) to work in Xubuntu. 

1.) I logged out of Xubuntu. 
2.) Logged back into the Unity desktop. 

Once I was using the Ubuntu desktop, I could access the *Sound* settings under *System Settings*, but the Mic was already working without any further tweaking. :-k 

1.) I logged out of Ubuntu-Desktop
2.) Logged back into Xubuntu.

The mic now works.

This makes me think that your solution is Unity (or Gnome) specific, or at least doesn't seem to work in Xubuntu (without further investigation).

**Edit: **So, if you don't mind my asking, what does this additional line _do_ exactly?

---

### Post by aimwin on 2012-07-08
Sorry to be repeating,
To be precised, 
you did put ==>
options snd-hda-intel model=auto enable=yes
in the last line of
sudo gedit /etc/modprobe.d/alsa-base.conf
===> in both partition, XUBUNTU and UBUNTU,
OR you did that only in XUBUNTU.

And it make Mic worked in Unity Ubuntu even without
 options snd-hda-intel model=auto enable=yes
in Uinity Ubuntu

Thanks

---

### Post by neu5eeCh on 2012-07-08
> **aimwin said:**
> Sorry to be repeating,
To be precised, 
you did put ==>
options snd-hda-intel model=auto enable=yes
in the last line of
sudo gedit /etc/modprobe.d/alsa-base.conf

Yes.

> **aimwin said:**
> ===> in both partition, XUBUNTU and UBUNTU,
OR you did that only in XUBUNTU.

And it make Mic worked in Unity Ubuntu even without
 options snd-hda-intel model=auto enable=yes
in Uinity Ubuntu

No. Xubuntu and Ubuntu are both on the same partition and are chosen at log in. I am running both DE's on the same partition. I normally use the Xubuntu DE.

I modified alsa-base.conf while logged into the Xubuntu DE. I _rebooted_. The internal microphone, after rebooting and logging *back *into Xubuntu, worked; but the external microphone _did not_. I logged out of Xubuntu and logged back into Ubuntu (_not_ rebooting). Once I was in the Ubuntu-Desktop session (unity), the external microphone worked without any further tweaking. I logged out of the Ubuntu session, and back into the Xubuntu session (_not_ rebooting). Once I was back in the Xubuntu session, the *external* mic continued to function correctly.

---

### Post by aimwin on 2012-07-08
WoW,
I will try your way one day, 
double Desktop in the same partition.

============

I understood your result now.

Please confirm too,
since I am new in these DE du-o,
that both DE use the same alsa-base.conf then.????

==============================================

My dv1000, dv1729TU to be specific, has no internal Mic & camera.
So I have to change the setting in "Sound" setting to choose,
"Line IN" in order my external mic, from Mic Jack, to work.

If I left it at Microphone as default in the input device,
then no sound for Mic Jack.
Only option with "Line In" will enable sound for the Mic Jack.

Thank you for details explaination.

---

### Post by neu5eeCh on 2012-07-08
Well... it's interesting. The External Mic works beautifully on the Xubuntu side, but I can't switch it to the internal Mic. I have a hunch, though, that if I logged out and back into Ubuntu Desktop/Unity, I could switch back and forth between the internal and external mic. At this point, this seems to be a problem with XFCE/Xubuntu?

The only reason I ever have to use the internal Mic is during screen capture sessoins, which I maybe use once a year.

---

### Post by neu5eeCh on 2012-07-08
> **aimwin said:**
> 

I understood your result now.

Please confirm too,
since I am new in these DE du-o,
that both DE use the same alsa-base.conf then.???? 

Yes, they *should*. They are both "Ubuntu".  But how they access that alsa-base-conf is apparently different.'

This is about the time for the wonderful wizard of Toz to step in.

> **aimwin said:**
> My dv1000, dv1729TU to be specific, has no internal Mic & camera. So I have to change the setting in "Sound" setting to choose,
"Line IN" in order my external mic, from Mic Jack, to work. 

I have a strong hunch that the problem is in my using the "_Pulse Audio_ Volume Control" center when I *should* be doing it through alsa. I think that's the key to the whole thing. I'm still not sure how to proceed with this supposition. Working on that.

**Edit: **Yes, that's the issue. As soon as I added the line to alsa-base.conf, the microphone app showed up on my XFCE 4.10 panel. If I use **that** to record with (rather than Audacity or Pulse Volume Control Center) then I can switch between the Internal and external microphones.

---

