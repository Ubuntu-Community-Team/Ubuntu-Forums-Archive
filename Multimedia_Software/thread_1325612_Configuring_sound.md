---
title: "Configuring sound"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Stuart P. Bentley on 2009-11-13
How do I change the startup sound on Karmic? Going to System->Preferences->Sound only lets me choose one of four alert sounds.

---

### Post by Stuart P. Bentley on 2009-11-14
Here's the way I did it:

Go to /usr/share/sounds/ and create a directory for a new sound theme with your customizations. (The directory is owned by root, so you'll have to find a way around it: what I did was run (Alt+f2) "sudo nautilus /usr/share/sounds;" in a terminal (so I could input my password to sudo). There might be a better/easier way to properly work with directories as root, but this is the one I went with.)

Make an index.theme file inside this folder to the [FreeDesktop Sound Specification]("http://0pointer.de/public/sound-theme-spec.html#background"). (The easiest way to do this is to copy the one out of /usr/share/sounds/ubuntu/ and edit it with gconf (I repeated the steps to sudo nautilus for gconf and opened the new file from the window) changing "Ubuntu" to the name of your custom theme. If you're not replacing every sound, you might want to add the line "Inherit=Ubuntu" in the Sound Theme section so you still use Ubuntu's sounds for everything you don't specify). Also, make a "stereo" folder for your stereo sound file(s) (and/or a 5.1 folder, if you've got it- make sure it's in your index.theme (in your directories and with a section defining your OutputProfile).

To replace the specific sound you're looking for, find its filename under /usr/share/sounds/ubuntu/ (it'll probably be fairly descriptive, but make sure to hover over it for the preview to be sure), and place your sound in your theme's stereo (and/or 5.1) folder with the same filename. (The extension doesn't have to be the same if your file is a WAV or maybe MP3 instead: however, for consistency and efficiency's sake, I recommend getting Audacity off the Ubuntu Software Center and saving it as an Ogg Vorbis .ogg file, with the Quality on export set to "1" (80 Kbps).)

Finally, go into System -> Preferences -> Sound (or right-click the volume applet and choose "Sound Preferences") and, under the "Sound Effects" tab, change the "Sound Theme" dropdown to your theme (it should be there with the name you defined in the index.theme file).

To apply this theme to the login screen (so it will play your system-ready sound), run this command (based from [http://ubuntuforums.org/showpost.php?p=7576112&postcount=365):](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365):)
> sudo -u gdm gconftool-2 --set --type string --set /desktop/gnome/sound/theme_name <*your theme's folder name>*

---

### Post by jstars on 2009-11-19
Wow... talk about a usability shortfall. Appreciate your work-through but if this is the easiest way of doing something like changing the login sound, then Gnome/Ubuntu has some work to do.

---

### Post by Tedward on 2009-11-19
It used to be violently easy to do, I'm kind of disappointed they ruined it like this.

-edit
Well I guess it's not THAT ruined.  It took me 2 minutes longer to get it working how I wanted to than it used to, but it still works the same :)

---

### Post by BrMBr on 2009-11-19
I HATE karmic SOOOOO much! :mad:

---

### Post by GrandpaLeaman on 2009-11-19
> **BrMBr said:**
> I HATE karmic SOOOOO much! :mad:

Hmm, I dual boot Karmic and Vista. Karmic runs flawlessly for me, and the support for my Intel video card is excellent. Vista was what drove me to try linux over two years ago, and I have not looked back. There is just NOOOOO comparison between the two.

---

### Post by Stuart P. Bentley on 2009-12-12
Now I'm getting a problem with this where it gets reverted after updates. Is there any way to avoid this?

---

