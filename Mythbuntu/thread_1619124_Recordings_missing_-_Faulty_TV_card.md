---
title: "Recordings missing - Faulty TV card?"
date: 2010-11-11
forum: Mythbuntu
---

### Post by Sctmon on 2010-11-11
My Mythtv system seems to randomly mis recordings. The entry in the recordings list is there but with no thumb nail image and attempting to play it gives a file not found dialogue. 

I have found that after a recording like this has appeared, if I start to watch live TV and then change the tuner to input 2 it just stays on Partial Lock and does not tune to the channel. The only way to recover from this is to shut down, turn of the power to the computer for a few seconds and then boot up again.

It does occasionally happen on tuner 1 and sometimes on both.

The card I am currently using is a Haupagge Nova-T-500 DVB-T but I am reluctant to point the finger at it and as faulty yet.

I do live in a bit of a valley with generally poor reception but have a decent antenna and get good signal strength and quality, although all of the DVB-T boxes in the house suffer from the occasional stutter whilst watching programs.

Does this sound like some kind of signal spike possibly causing the tuner card to crash? 

I would welcome any recommendations for a decent twin DVB-T card that is compatible with Mythtv, preferably PCI-e but anyhting that is stable.


I would post the log files from my backend but they only show the recording starting on time, finishing on time and me trying to play the file which is not present.

---

### Post by ian dobson on 2010-11-11
Hi,

If your problem is really a low signal strength, then maybe enabling the amplifier might help. See
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

and 
Forcing the activation of LNAs (Low Noise Amplifier) 
You may have to force LNA to get this card working: 

In /etc/modprobe.d/options add: 

options dvb_usb_dib0700 force_lna_activation=1

Regards
Ian Dobson

---

### Post by Sctmon on 2010-11-11
Does this enable an internal signal amplifier or send a dc voltage to a masthead amplifier? I will have a look at the link later when I am back at the computer (on my phone now)
My antenna has a masthead amp powered by a small inline power supply. Would turning the LNA interfere with that?

---

### Post by ian dobson on 2010-11-11
Hi,

I think it just enables the onboard amp in the card. It shouldn't affect your external amp.

Regards
Ian Dobson

---

### Post by Sctmon on 2010-11-13
I have just gotten round to trying to turn on the LNA but there is no options file. I have just created an empty file called 'options' (should it be options.conf?) and added 'options dvb_usb_dib0700 force_lna_activation=1' to it, then rebooted. Is there a way to to check that it is actually enabled?

After a bit of research it does seem like the Nova-T-500 card locking up requiring a cold boot is a know issue.

---

### Post by ian dobson on 2010-11-13
Hi,

it should be something.conf for it to be read by modprobe.

Regards
Ian Dobson

---

### Post by Sctmon on 2010-11-13
For the benefit of anyone else reading, I believe you have to reconfigure the kernel for the changes to take effect (may be wrong though)

sudo dpkg-reconfigure linux-image-2.6.32-25-generic (or whatever kernel you are using uname -a should tell you)

---

### Post by PhilWig on 2010-11-22
A cold reboot (ie remove power from the system for about 10 secs) is enough to reset my T500 card and force a microcode reboot and adoption of the amplifier setting.   Oddly, I also have to do this if I switch from VGA output to HDMI. No idea why.  
I did at one stage have problems with failed recordings - error 2060 which were fixed by setting tuning delay to 500 ms on the first tuner and to 1000 on the second.  The card is now very stable apart from the remote control.

You might find this source interesting - he also suggests raising tuner delay, but less aggressively.
[http://www.youplala.net/linux/home-theater-pc#toc-not-losing-one-of-the-nova-t-500s-tuners](http://www.youplala.net/linux/home-theater-pc#toc-not-losing-one-of-the-nova-t-500s-tuners) 

Phil

---

### Post by Sctmon on 2010-11-22
Hi,
Thanks for the info. I will try adding the delays in and see what happens but it has been fairly stable lately. I am assuming that the LNA is enabled now but I am not sure how to check if that is the case.

Since I got my Android phone I have been using MythMote and MythDroid to control the system and my wife uses her iPod Touch. It is certainly a lot easier than the old IR keyboard and Harmony learning remote control I had been using.

---

