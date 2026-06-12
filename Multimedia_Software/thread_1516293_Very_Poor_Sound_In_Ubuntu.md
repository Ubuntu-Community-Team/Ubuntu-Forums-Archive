---
title: "Very Poor Sound In Ubuntu"
date: 2010-06-23
forum: Multimedia Software
---

### Post by mrphud on 2010-06-23
Hi,

I just installed Lucid. I am getting sound from the start-up but when I try to play online videos like youtube, or music, the sound quality is very poor. The audio will start by skipping/glitching and then stop completely. 

I have a Hercules Game Theater XP sound card that is recognized by Ubuntu with the CS4630 driver assigned to it. I believe that the driver just has poor compatibility. There are several ports for my sound card that I can use for input from various devices, including my TV tuner, and none of them work.

Is this the issue? What should I do?

Thanks

---

### Post by mrphud on 2010-06-24
Really? Not help at all? Does this mean there is no fix for this? I would hope that someone might know how to deal with driver issues. Is there a way to use the driver for XP to help? Can I somehow look at the XP settings and modify the linux driver to mirror? 

This is the only real problem with this system. I would hate to give up on linux because I can't hear anything from my computer.

---

### Post by passonno on 2010-06-24
Patience....  

Can I suggest you also post your question to linuxquestions.org?

And I will do some research for you as well,  but remember that Google is going to be far more helpful for a relatively obscure piece of hardware than the Ubuntu Forums.

Good Luck

---

### Post by passonno on 2010-06-24
[http://bit.ly/ceXetK]("http://bit.ly/ceXetK")

Here's a start,  though it's really old.

---

### Post by passonno on 2010-06-24
One More:[http://bit.ly/cRo0Mb]("http://bit.ly/cRo0Mb")

---

### Post by lidex on 2010-06-24
Start here: Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by mrphud on 2010-06-24
I entered the above command into the command line and this is what I got.


```
sudo bash utils_also-info.sh
[sudo] password for jordan: 
bash: utils_alsa-info.sh: No such file or directory
```

I wish I knew what it meant.

---

### Post by mrphud on 2010-06-24
wow thanks passano. Those are great links. I can't believe I didn't find them before. 

With the research I did today I have been able to make some progress.

Now, the TV tuner works as it plugs into an aux input in the back of the PCI card. I have been able to get the mic, headphones, and all speakers working. I got this all done using alsamixer

The problem now is that, even though I have sound in all speakers, I have very poor quality still. Meaning I get skips and reverbs and pops and eventual failure of sound. This happens when I play audio files, flash videos, or DVDs.

Apparently, this card works great under linux so it must be a config issue. 

So... what now?

---

### Post by mrphud on 2010-06-24
> **lidex said:**
> Start here: Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

Sorry but what is my sig? I am running 10.04. Where is that?



OK, Sig must mean post or something. I figured it out. I am posting now.

---

### Post by mrphud on 2010-06-24
```
sudo bash utils_alsa-info.sh 
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : 

```

OK This is what came out after I ran the file. Now where do we go?

---

### Post by lidex on 2010-06-25
At that stage you would enter y or n and hit enter key. For convenience just go with y and it will upload the results to the alsa website. Then post the link it gives you here.

---

### Post by mrphud on 2010-06-25
OK. I submitted to ALSA but it never gave me an address to check it out at. So I searched and found a post where a person submitted to pastebin. This gave me a link. The code is below.

[http://pastebin.ca/1889321]("http://pastebin.ca/1889321")

```
bash utils_alsa-info.sh --pastebin
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to pastebin? [y/N] : y
Uploading information to www.pastebin.ca ...  Done!

Your ALSA information is located at http://pastebin.ca/1889321

Please inform the person helping you.

```

---

### Post by Moozillaaa on 2010-06-25
Do you have settings in BIOS for sound card configuration that are conflicting with ALSA?

I've seen on some machines with advanced sound cards, a BIOS configuration that changes a mic port (input), into a center channel OUTPUT...

---

### Post by mrphud on 2010-06-25
I don't believe a BIOS conflict is the issue. After playing with alsamixer I am able to get sound from Headphones, mic and speakers (all with clear sounds) when they are playing from my TV tuner. The problem is that any sound coming from my computer, like internet, mp3, etc.., has to bad sound. 

This makes me think it is some codec issue or data processing issue. The sound card appears to work like normal when I have an external source feeding it.

Hmmmmm

Also, pulseaudio keeps giving me a failure notice like "connection failed; connection terminated". I wonder if they are related.

---

### Post by lidex on 2010-06-25
If you have installed alsa-backports, please uninstall it. Next upgrade your alsa install using the link in my sig (alsa-upgrade-script). I'm having some issues with the online version of your alsa-info text. Would you please run the script again **after the update** and save it locally, then upload as an attachment in a follow-up post. The terminal output will give the location - should be in your /tmp directory.

---

### Post by mrphud on 2010-06-25
OK. I updated to the new ALSA. 1.0.23-2 and ran the info script again.

Here is the file.

---

### Post by lidex on 2010-06-25
Some of your levels are really cranked up. That could easily cause distortion. When did you add the /etc/asound.conf file? Try moving/renaming it then logout/in. Do you have problem with volume levels, is that why it's cranked up?
Have a look at this. 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

There is an external amp option for this card, look for that or eapd. It looks like it's currently disabled. If you need the amplification for good levels that could be the problem.

---

### Post by mrphud on 2010-06-25
All looks good. I used the terminal alsamixer before. I turned down the levels but that is not the issue. I have an external volume control for the sound.

The issue is the sound quality and eventual failure of sound. It starts off garbled - if at all - and then eventually stops working. Also, when I open pulseaudio manager and play sound the connection eventually terminates. Even sometimes when I don't play sound. 

I know this card has work in previous ubuntu distros. And I know alsa supports this card. I just don't know where the glitch is when I play files on the computer. Like I said my TV tuner transmits sound through my audio card and that works fine.

Thanks

---

### Post by mrphud on 2010-06-25
Hey Hey.

We are making some progress!!!

I can now hear clear audio through youtube. I can only hear it on two speakers but some is better than none eh?

This means we have something to work with right?

What next!!!!

---

### Post by lidex on 2010-06-25
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

### Post by mrphud on 2010-06-25
OK. Done.

OK. We are almost there!! Now I get nice clear audio but only out of two speakers and subwoofer. Plus the pulse audio icon doesn't work. It refuses all connections.

So now where?

Should I just uninstall pulse audio?

---

### Post by lidex on 2010-06-25
Go here and follow the howto to setup pulse correctly:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

Do part A, skip no.1 which you just did.

---

### Post by mrphud on 2010-06-25
I removed this post because it was not right. The next post is the most current situation.

---

### Post by mrphud on 2010-06-26
OK. I figured out why I am only playing two speakers. This is because pulseaudio is set to analogue stereo duplex. I found this out because I rebooted my system and was able
to open pulseaudio. So.... I thought I would try and play with 4.1 audio setup (as that is what I have) and it goes back to the poppy poor sound as before. What I did was switch to 4.1 output and restarted the comp. The sound is poppy. I switch back to duplex and restart. The sound is clear but only through two speakers.

Does this tell us anything?

---

