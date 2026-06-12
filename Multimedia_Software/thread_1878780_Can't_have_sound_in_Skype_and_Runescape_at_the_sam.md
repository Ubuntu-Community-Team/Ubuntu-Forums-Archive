---
title: "Can't have sound in Skype and Runescape at the same time"
date: 2011-11-10
forum: Multimedia Software
---

### Post by Miora on 2011-11-10
The basics: I use Lucid Lynx and have a Logitech webcam that shows up as 081d in Sound Preferences. I use Sun Java but that doesn't seem to matter much as the precise same results occur with the openjava. The browser here is Firefox 8.0

I have this problem since....well not since forever because somewhere before halloween I used to be able to play Runescape and talk to my friend on skype at the same time.
But somewhere after that it suddenly stopped.. Quite strange because I don't recall changing any settings.. Although I do remember that when I first configured skype there where more sound options.... *insert Twilight Zone theme here ;)*

When I log in to RS while skyping I will have no sound in RS.
When I pick up a skype conversation while playing RS There is no sound in the conversation.

Skype seems to use pulseaudio and it won't let me select anything else.
I notice in the Sound Preferences that under the Application tab there will be 2 skype instances.
An ALSA plugin is used when I play anything on YouTube but that's no problem as I can play YouTube video's and call on Skype at the same time just fine.
When playing Runescape and it does play sound then no application appears in that tab. 

I'm guessing that Pulseaudio seems to distrubute the sound wrong. But I have no idea how to change that.
And perhaps would it be a good idea to remove Pulseaudio and get back to ALSA someway?

---

### Post by Miora on 2011-11-11
Well, removing pulseaudio didn't do it so far.
And any help would be greatly appreciated, pretty please!!!

---

### Post by Truckerpunk on 2011-11-13
In all the previous releases of Ubuntu I've been able to get my java sound working nicely by adding an audio-wrapper to the java script. It has always been successful to do the following work around:

cd /usr/lib/jvm/java-YOURVERSION-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java

And then making the script:

#!/bin/bash
padsp /usr/lib/jvm/java-YOURVERSION-sun/jre/bin/java.bin "$@"

you can change the padsp to aoss for your setup if needed.

---

### Post by Miora on 2011-11-15
Do you mean I should add the padsp to /bin/bash?

And how do I know wether to use padsp or aoss?

---

### Post by HanErli on 2012-04-15
> **Miora said:**
> Well, removing pulseaudio didn't do it so far.
And any help would be greatly appreciated, pretty please!!!

When removing pulseaudio, you need to restart your computer before the removal takes effect.

After that, the problem is solved. Except now you can't use the panel to control your volume, because the icon is gone (and even when you reinstall the icon on the panel you can't use it. You can only control volume through alsamixer (which is VERY inconvenient). Don't worry, though, you can always reinstall pulseaudio.

What I REALLY want though is a way to either allow pulseaudio to work with skype AND another sound source from your browser OR to be able to temporarily disable pulseaudio (perhaps through a script). The first is obviously better, though.

---

