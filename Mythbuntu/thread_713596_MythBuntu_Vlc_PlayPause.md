---
title: "MythBuntu Vlc Play/Pause"
date: 2008-03-02
forum: Mythbuntu
---

### Post by Angryartichoke on 2008-03-02
I have recently switched from mplayer to vlc in mythtv.

The remote im using (The one that comes with the PVR-150 MCE) works fine, except for one issue. I need to find a way to change the play/pause so it isnt a toggle function. It pauses fine, using either the pause or play button. But when i go to play it again, neither of the two will resume the video.

How do I make it so that pause ONLY pauses, and play ONLY plays?

Thanks!

---

### Post by newlinux on 2008-03-03
> **Angryartichoke said:**
> I have recently switched from mplayer to vlc in mythtv.

The remote im using (The one that comes with the PVR-150 MCE) works fine, except for one issue. I need to find a way to change the play/pause so it isnt a toggle function. It pauses fine, using either the pause or play button. But when i go to play it again, neither of the two will resume the video.

How do I make it so that pause ONLY pauses, and play ONLY plays?

Thanks!

Modify your .lircrc file to have the play key use key-play and the pause key to use key-pause instead of having them use key-play-pause.

---

### Post by Angryartichoke on 2008-03-04
I'm having trouble finding the lircrc file. Where do I modify the lircrc settings for the VLC plugin? There's one in /lirc/contrib/ which has the following:

#
# defaults:
#
# remote = *
# repeat = 0
#
#
#

begin
	button = MENU
	mode = mouse
end

begin
	prog = xirw
	button = MENU
	config = Mouse aktivieren
end

begin
	prog = irexec
	button = 1
	button = 2
	button = 3
	button = 1
	button = 2
	button = 3
	button = 4
	config = echo "secret code"
end
begin
	prog = xirw
	button = 1
	button = 2
	button = 3
	button = 1
	button = 2
	button = 3
	button = 4
	config = psssst, secret
end

begin
        prog = irexec
        button = VOL_UP
        config = mix vb+5 >/dev/null
end
begin
	prog=xirw
	button = VOL_UP
	config = Lautstärke +
end

begin
	prog = irexec
	button = VOL_DOWN
        config = mix vb-5 >/dev/null
end
begin
	prog=xirw
	button = VOL_DOWN
	config = Lautstärke -
end

begin 
	prog = irexec
	button = TV/R
	config = xawtv  -geometry +754+0 >/dev/null&
	mode = tv
	flags= once
end
begin
	prog=xirw
	button = TV/R
	config = Moduswechsel
end
begin
	prog = irexec
	button = A/B
	config = kscd -geometry +60+600&
	mode = cd
	flags = once
end
begin
	prog=xirw
	button = A/B
	config = Moduswechsel
end
begin
	prog = irexec
	button = BACK
	mode = system
end
begin
	prog=xirw
	button = BACK
	config = Moduswechsel
end

begin tv
	
	begin
		prog = irxevent
		button = 0
		config = Key f xawtv
		config = Key f xawtv
	end
        begin
                prog = xirw
                button = 0
                config = Vollbild an
                config = Vollbild aus
        end
	begin
                prog = irxevent
                button = POWER 
                config = Key Escape xawtv
	end
	begin
		prog = xirw
		button = POWER
		config = TV beenden
		flags = mode
	end
end tv

begin cd
        begin
                prog = irxevent
                button = OK
                config = Button 1 51 31 kscd
        end
        begin
                prog = xirw
                button = OK
                config = Display
        end
        begin
                prog = irxevent
                button = CH_UP
                config = Button 1 376 92 kscd
        end
        begin
                prog = xirw
                button = CH_UP
                config = Nächster Titel
        end
        begin
                prog = irxevent
                button = CH_DOWN
                config = Button 1 329 92 kscd
        end
        begin
                prog = xirw
                button = CH_DOWN
                config = Vorheriger Titel
        end
        begin
                prog = irxevent
                button = ARROW_DOWN
                config = Button 1  70 70 kscd
        end
        begin
                prog = xirw
                button = ARROW_DOWN
                config = Eject
        end
        begin
                prog = irxevent
                button = ARROW_UP
                config = Button 1 360 13 kscd
        end
        begin
                prog = xirw
                button = ARROW_UP
                config = Play
		config = Pause
        end
        begin
                prog = irxevent
                button = ARROW_RIGHT
                config = Button 1 370 63 kscd
        end
        begin
                prog = xirw
                button = ARROW_RIGHT
                config = FWD
        end
        begin
                prog = irxevent
                button = ARROW_LEFT
                config = Button 1 332 69 kscd
        end
        begin
                prog = xirw
                button = ARROW_LEFT
                config = BCK
        end
        begin
                prog = irxevent
                button = MUTE
                config = Button 1 338 43 kscd
        end
        begin
                prog = xirw
                button = MUTE
                config = Stop
        end
        begin
                prog = irxevent
                button = POWER
                config = Button 1  51 92 kscd
        end
        begin
                prog = xirw
                button = POWER
                config = CD beenden
		flags = mode
        end
        begin
                prog = irxevent
                button = 0
                config = Button 1 379 45 kscd
        end
        begin
                prog = xirw
                button = 0
                config = Loop
        end
        begin
                prog = irxevent
                button = LIST
                config = Button 1 160 99 kscd
        end
        begin
                prog = xirw
                button = LIST
                config = Random
        end

end cd

begin system
        begin
                prog = irexec
                button = POWER
		config = xset dpms force off
		config = xset dpms force on
        end
        begin
                prog = xirw
                button = POWER
                config = Bildschirm abschalten
                config = Bildschirm anschalten
        end
        begin
                prog = irexec
                button = MUTE
                config = sync;hdparm -y /dev/hda >/dev/null
        end
        begin
                prog = xirw
                button = MUTE
                config = Festplatten abschalten
        end
        begin
                prog = irexec
                button = CH_UP
		config = xvidtune -next
        end
        begin
                prog = xirw
                button = CH_UP
		config = Auflösung +
        end
        begin
                prog = irexec
                button = CH_DOWN
		config = xvidtune -prev
        end
        begin
                prog = xirw
                button = CH_DOWN
		config = Auflösung -
        end
end system

---

### Post by newlinux on 2008-03-04
You should have a file:

```

~/.lircrc

```
For the user you run VLC as. This is the file you want to modify. if you are unsure of what to modify there, post the contents back to this thread...

---

### Post by Angryartichoke on 2008-03-08
Ok, I finally got it.

Apparenly I was trying to edit it incorrectly. When I typed "sudo gedit /lircrc" in console, it would give me a blank file. (because the path was incorrect). Then I tried "sudo gedit .lircrc" which had the lircrc config buttons for all the mythtv plugins.

I then change play's setting to config=key-pause

For some reason, this didn't work, so I changed it to config=key-play-pause

Play now toggles play/pause, which works perfectly for me. I'm not sure why it didn't before. I set pause to stricly pause (config=key-pause)

Anyways, thanks for the help!

---

