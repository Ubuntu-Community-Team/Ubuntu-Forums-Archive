---
title: "[SOLVED] Headphone not working with Acer-Aspire-AS6530-5195"
date: 2008-12-24
forum: Multimedia Software
---

### Post by dave.mueller on 2008-12-24
Hello Everybody.

I have an Acer-Aspire-6530-5195 laptop, running ubuntu 8.10. When I plug in my headphones, I would hope to get sound through them, and not through the laptops built in speakers, but that is not working.  Headphones plugged in, sound comes from the speakers, and not from the headphones.

Searching from google lead me first to this thread:
[http://ubuntuforums.org/archive/index.php/t-862980.html](http://ubuntuforums.org/archive/index.php/t-862980.html)

and subsequently to this thread:
[http://ubuntuforums.org/showthread.php?p=6115891#post6115891](http://ubuntuforums.org/showthread.php?p=6115891#post6115891)

I have at this point tried adding the suggested line to the alsa config file, and also tried several variations with the model=XXXX line based on information in [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

But all to no avail.  I have also experimented with the settings in the sound section under preferences with no success.

I have a fair amount of experience with fedora, but I am new to ubuntu, and any suggestions on what to try next would be greatly appriciated.

Thank you!

---

### Post by dave.mueller on 2008-12-24
solved:

see this thread:
[http://ubuntuforums.org/showthread.php?p=6079516&mode=linear&highlight=headphone#post6079516](http://ubuntuforums.org/showthread.php?p=6079516&mode=linear&highlight=headphone#post6079516)

---

### Post by hope2contribute on 2009-08-31
Acer-Aspire- 6530: Heandphone and Sounds

Solved but Unsat. 

There is no driver for this as far as I know. Thanks to this forum, I was able to adjust sound from my speaker to my headphone and vis versa. Here are the steps to solve the headphone and speaker problem:

1. Click on speaker control icon on your task bar.

2. Click on "**Volume Control**..." 

3. A new window should pop out. Select the "Device": "**HDA ATI SB (Alsa Mixer)**"

4. Select the option "**Playback**" after you have selected HDA ATI SB (Alsa Mixer) on step #3.

5. Click "**Preferences**," the "Volume Control Preference" window should pop out.

7. After the "Volume Control Preference" window open. Make sure the following are checked:
[B]-Master
-PCM
-Front
-Surround[/B]

 (Step 8+, assume Master Volume is at 100%)

8. Increase the "**Surround**" volume 100%, (this will allow sound to travel to your headphone)

9A. Increase the "**Front**" volume to 100% will increase your PC speaker volumes 
9B. Increase the "**PCM**" volume to 100% will increase your volume on your head phone.

10. Switching between headphone and pc speaker is a matter of mute/dis-mute. Notice, you can have sounds to your headphone and pc speaker at the same time. If you want to mute the pc speaker and only listen o headphone, you will need to mute the "Front" volume. If you need to turn the sound on again, just unmute it. 

**[COLOR=Red]Please REFER to attachment for Step 10.[/COLOR]**

Thanks for all those who contributed. :popcorn:

---

### Post by Luuna on 2009-09-27
Hi !

I'm having a similar problem with Ubuntu 9.04 : nothing happens when I plug headphones in. I would like to try your "surround" solution but it does not appears in my Volume control preferences (in screenshot). Any tips as to making it come ?

Computer : HP dv7-2065ef laptop with a front headphone plug in
I've got the latest AlsaMixer version on.

Thanks !

---

### Post by ijse on 2010-07-01
i have the same problem, almost the same..

i think the reason for this is that we have no the righ driver .

by the way, i am using the Acer Aspire 6530

---

