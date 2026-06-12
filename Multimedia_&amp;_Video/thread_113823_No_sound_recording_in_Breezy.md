---
title: "No sound recording in Breezy"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by fdimmling on 2006-01-07
I used to make CDs from old vinyl records by the USB soundcard iMic and gramofile which worked fine in Hoary. 
In Breezy though the recording-level indicates signals coming in neither gramofile nor gnome-sound-recorder or sweep get any sound.
I have seens that there were some threads on sound recording in Breezy here before without solution. I would like to keep this problem on the table. Maybe some time an expert finds a fix.

Friedrich:rolleyes:

---

### Post by mpvano on 2006-01-07
If by "recording level" you mean the "recording level monitor" application in the "sound & video" menu, then the fact that it is working indicates that the "esound" daemon is in use in your system.

This hidden application prevents normal sound programs from working since it takes over full control of your sound ports to allow them to be shared so that gnome can make UI sounds while sound programs are in use.

You can check for its presence by looking for a process called "esd" in the list of running programs. If it's there, your OSS and ALSA software cannot work until you force it to be removed by using the kill command or system monitor program.

Try going to the multimedia preferences menu and setting default source and sink to OSS so that programs that check the preferences do OT use esound. Then go to the sound preferences menu and disable "sound server startup".

Once you have made these changes and made sure the daemon is not running, You will also need to make sure that no sound generating program you use causes the daemeon to be reloaded - unfortunately many ubuntu versions of common programs have been modified to try to use the esound system as their first choice and to try to load the daemon if it's not already running. You can usually find out if this is the case by carefully studying the man page and any preferences dialogs for the programs.

If you are using kubuntu, the situation is similar but the daemon system is called "arts".

Either of these "take no prisoners" sound api systems break all sound programs that do not use them. Unfortunately the designers of Gnome and KDE have both decided that they are mandatory for use of their GUI systems at the moment.

hope this is your problem - it's actually pretty easy to work around!

Mario

---

### Post by fdimmling on 2006-01-07
[QUOTE=mpvano]If by "recording level" you mean the "recording level monitor" application in the "sound & video" menu, then the fact that it is working indicates that the "esound" daemon is in use in your system.
[/QUOTE]

Yes. I was talking about the "recording level monitor". I'm using a German Ubuntu - sorry. Actually I had tried do solve the problem by disabling esd but it did not work so far. Maybe the difference to Hoary is the follwing point which prevents gramofile from getting sound input. Gramofile seems to fetch its data invariably from sound card 0. I use an Acer laptop with a builtin soundcard which is of no use and an iMic USB soundcard. In Hoary this USB soundcard become card 0 when it was connected at boot time which made it available for gramofile. In Breezy it is card 1 regardless of the time I connect it. I have checked it by looking at .asoundrc while changing the default sound card with system->preferences->audio.
Maybe I have to force the USB device to card 0 by making an appropriate .asoundrc which may produce other problems e.g. with Skype where I use an USB headset.

Friedrich:rolleyes:

PS Killing esd at least gives me sound input in sweep

---

