---
title: "alsa + pulseaudio notes"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Claus7 on 2009-11-02
Hello,

since karmic things are shaping to take a clearer picture on sound settings. Yes, I do know that things are getting more complicated and for some, sound is a past and good memory. So, here, I will give some notes on the subject. 

They are not going to include commands or whatever. Just some guidance on what someone should look first and easily in order to be able to configure sound. Things are told having karmic as a reference, so I do not know whether they will work in jaunty too.

So, for sound to work both alsa and pulseaudio should work, if both of them are installed. There might be a possibility that you get no sound because one of them is muted.

[CENTER]**ALSA**[/CENTER]
The first thing (easy to check) is to open a terminal and type the magic command:
alsamixer

With this you will see many many bars filling your terminal.
Like...[COLOR="RoyalBlue"]fig1_alsa[/COLOR]

There you should pay attention to three different things:
1) In the card section (left hand up) you should see the type of your sound card. If you have more than one card, then the default one (the one you want to use) should be there. If not, then you are using a wrong card.
2) The master bar should not be at 0% or 100%, because that way the sound is buggy. Also in the base of the bar you can distinguish two "00". These should be as you see them. If you type m, while at a bar, then the channel that corresponds to that bar will become either muted or unmuted. In the first you will see two MM's in place of the 00's.
3) Also check out the PCM bar. This should not be muted as well... 

Other than that configure the other ones at your leisure.

[CENTER]**PULSEAUDIO**[/CENTER]

This is something new to our lives, since it did not exist at previous versions of Ubuntu. What you have to check out here is: (Applications -> Sound and Video -> PulseAudio Device Chooser)

1)There on Manager and the tab Sample Cache, you should be able to hear the samples. Check out the playback on option... [COLOR="#4169e1"]fig2_sample_cache[/COLOR]
2)On the volume control you can check many things. Here I didn't bother to configure anything, since all the other options where vital for my sound to work. In the tab output devices you should make sure that the correct sound card is there. 

[CENTER]**Sound Preferences**[/CENTER]

Here you can access your Preferences by the up right corner of your panel (in Desktop).
You have to choose under Hardware tab, the right setting for your sound card. Mine you can see it at the figures I provide.[COLOR="#4169e1"]fig3_pulse_hardware[/COLOR]
Also here, you have to check out the right option from the tab output. There, if you chose the wrong one, you won't have any sound... See also the figures I provide. [COLOR="#4169e1"]fig4_pulse_output[/COLOR]

Hope this helped a little...
Also I have to add that it is best to do configurations, while you are not hearing any sound. (Yet, how you will test it, ...?)
From my humble experience, every time I tamper with sound, while hearing something, the next time I open my pc, the settings are not the ones I had before closing down my computer. So, I hope you here good luck...

edit: If for some reason, sound stops working, the command:
killall pulseaudio
might do the trick(!)

Regards!

---

### Post by Claus7 on 2009-11-08
Hello,

I was fed up by trying to re-open sound via killall pulseaudio, and every time I open my pc to have different sound configurations. So here are my steps to have a descent sound quality:

[...]
who in the first place figured out that pulse should be implemented in Linux and Ubuntu? Since alsa was working pretty magnificently!
[..]

I have also to point out, that there are many many posts and threads concerning sound issues in karmic, which is really bad, since this should not have been a problem. Anyway, please spare me if I cannot comprehend why pulse is so necessary to Ubu systems and also so revolutionary.

So three steps would suffice:

1)Get rid of pulse
[http://ubuntuforums.org/showpost.php?p=8266465&postcount=5](http://ubuntuforums.org/showpost.php?p=8266465&postcount=5)
2)Do not hear yourselves though the speakers
[http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16)
3)Hear sound from all of your speakers (forget the weird sound issue in this post, with step 2 you get rid of it)
[http://ubuntuforums.org/showpost.php?p=1718248&postcount=4](http://ubuntuforums.org/showpost.php?p=1718248&postcount=4)

and your sound is rocking hard!

Luckily, because I was fed up all this time!
My kindest regards!

PS: Let's hope that amsn will make it finally with the chat-video support, and that flash player will work as it should. With a clear installment of karmic it had suggestions about which flash one prefers when one opens a browser...and the free one was working like a charm. Not bad, not bad at all!

---

### Post by szaemon on 2009-11-19
Oops! Sorry I'm sleepy and posted this in the wrong forum. please ignore it.

Let me answer your last question first as that may be quite pertinent to my problem. You asked about sound with earlier versions of Ubuntu. On this system I was not able to even install any earlier versions of Ubuntu due to some graphics incompatibility issues with the 
Intel 945G Express Chipset.

I did however have fully functioning sound with the Japanese Version of Windows XP Pro the system originally came with. 

>Can you see if by typing this command you can recognize in the top left corner of the window that appears your sound card? I mean: does alsa recognizes your sound card?

I believe this means it recognizes my HDA Intel Card, but with nothing more descriptive than HDA Intel, perhaps this is just some generic recognition. I don't know.


Card:HDAIntel                                                          
Chip:RealtekALC262                                                     View:[Playback]CaptureAll                                              Item:Master[dBgain=0.00]                                               


OK, so I guess alsa is recognizing my sound card. If these are the spec for my sound card:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1b.0 0403: 8086:27d8 (rev 01)

Then following the link you gave me, whatever my sound card needs would be listed in IHC7 link.

It reads

"Introduction for HDA Intel soundcard

There are two ways of getting Linux drivers to work, you can either compile them into the kernel or build them separately as modules. Read the Kernel-HOWTO for details of how to compile a kernel.

**You must turn on the sound support soundcore module.** This is in the kernel. Look in the sound drivers directory and it should be the first option. Most people enable the module setting. That way you can load and unload the module manually if you have multiple soundcards/&#8203;devices or if you intend to debug or use cutting edge software which may cause your drivers to halt sometimes. Of course it also means you have more control of your system.

Most modern distros come with soundcore compiled as a module. You can check this in numerous ways. The easiest way is to type:

       modinfo soundcore

[COLOR="Red"]If this command returns that you have this module[/COLOR], then you don't need to recompile your kernel. " 

I ran the code mentioned:
me@mycomputer:~$ modinfo soundcore
filename:       /lib/modules/2.6.31-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
[COLOR="Red"]description:    Core sound module[/COLOR]
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-14-generic SMP mod_unload modversions 586 
me@mycomputer:~$ 

So I guess I do have the module, so I don't need to recompile the kernel. But I do need to turn on the sound support soundcore module, which is in the kernel, in the sound drivers directory.

Where? Do I need to be a root user to access this section? I don't quite know where to look for the kernel or the sound drivers directory.

As for this information:

00:1b.0 0403: 8086:27d8 (rev 01)

I'm not sure what it means or how I can use it to help me.
What does it identify about my sound card?

As for Pulse Audio, I had already followed the instructions on how to remove it. Now I've just reinstalled it I put in the but the padevchooser, in doing so Synaptic told me it was removing a program called "esound" or some such thing.

So I opened the Manager.

Now in the Sample Cache Tab, I hear no sounds.

under the Modules Tab, everything is empty except Module alsa-card. It has a long line of stuff, but it won't let me copy and paste it...
The properties for the Module alsa-card does say "Autoloaded: NO". That may be important.

Last thing I&m going to try before I get to sleep tonight is the command:
killall pulseaudio

I think that's suppose to resart pulse audio or something.

Thanks again for taking an interest in my problem.

---

### Post by damilaredavids on 2010-01-19
> **Claus7 said:**
> Hello,

I was fed up by trying to re-open sound via killall pulseaudio, and every time I open my pc to have different sound configurations. So here are my steps to have a descent sound quality:

[...]
who in the first place figured out that pulse should be implemented in Linux and Ubuntu? Since alsa was working pretty magnificently!
[..]

I have also to point out, that there are many many posts and threads concerning sound issues in karmic, which is really bad, since this should not have been a problem. Anyway, please spare me if I cannot comprehend why pulse is so necessary to Ubu systems and also so revolutionary.

So three steps would suffice:

1)Get rid of pulse
[http://ubuntuforums.org/showpost.php?p=8266465&postcount=5](http://ubuntuforums.org/showpost.php?p=8266465&postcount=5)
2)Do not hear yourselves though the speakers
[http://ubuntuforums.org/showpost.php?p=1423407&postcount=16](http://ubuntuforums.org/showpost.php?p=1423407&postcount=16)
3)Hear sound from all of your speakers (forget the weird sound issue in this post, with step 2 you get rid of it)
[http://ubuntuforums.org/showpost.php?p=1718248&postcount=4](http://ubuntuforums.org/showpost.php?p=1718248&postcount=4)

and your sound is rocking hard!

Luckily, because I was fed up all this time!
My kindest regards!

PS: Let's hope that amsn will make it finally with the chat-video support, and that flash player will work as it should. With a clear installment of karmic it had suggestions about which flash one prefers when one opens a browser...and the free one was working like a charm. Not bad, not bad at all!

  i dont quite get it yet. i have tried all the work outs in the links and they have just compounded my problems. no sound icon again in the notification area and yet no sound from the system.  also my /etc/modprobe.d/alsa-base is empty. what i would do for sound...

---

### Post by Claus7 on 2010-01-19
Hello,

> **damilaredavids said:**
> i dont quite get it yet. i have tried all the work outs in the links and they have just compounded my problems. no sound icon again in the notification area and yet no sound from the system.  also my /etc/modprobe.d/alsa-base is empty. what i would do for sound...

As I have answered you in another thread, I would suggest you to start a thread on your own. Yet, as far as the icon is concerned, I do not have a sound icon in my panel too, after following the links I suggested just above. Yet, my sound is working pretty nicely.

Regards!

---

### Post by ratcheer on 2010-01-19
Thank you for this thread. It is very informative. I have a question, please.

First, my sound is working just fine, but I am trying to learn about this stuff and I poke around while trying not to mess anything up. When I try to start the PulseAudio Device Chooser, as suggested in the original post, I get a "waiting" cursor for about 20-30 seconds, then the cursor turns back to normal and no PA Device Chooser ever starts. However, if I start PulseAudio Volume Control, it starts immediately and everything works as it should.

Any idea why PA Device Chooser is not working and what I should do to fix it?

Thanks,
Tim

---

### Post by ratcheer on 2010-01-19
Never mind. The "PulseAudio Applet" does seem to be starting. But, instead of opening an evident window on the screen, it is just putting a faint icon in the panel at the top right of the screen. So, I have found it, now.

Sorry,
Tim

---

### Post by lyall on 2010-04-27
thanks Claus7
do Get rid of pulse
and now when I boot my PC I have sound again with going into GNOME alsa mixer
and unmuting Master, Master M and PCM

thanks again

---

