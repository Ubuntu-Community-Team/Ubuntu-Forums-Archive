---
title: "Nautilus-Scripts-Audio-Convert can't batch now?"
date: 2015-02-16
forum: Multimedia Software
---

### Post by em3raldxiii on 2015-02-16
I have been a long-time user of the nautilus-scripts-audio-convert script.  For those who are unfamiliar, it's simply a script that allows you to right-click on any audio file in a file browser window and quickly convert its filetype.

It's been awhile since I last used it - perhaps since before I updated to 14.04 (which I am currently using).

Nowadays, when I right click on a batch of audio files (specifically FLAC files), the script does not show up in the Multimedia dropdown menu.  (I used to get a Scripts dropdown menu, but for some reason it's showing up as Multimedia now).

If I select ONLY ONE file, then the script _does_ show up, and I can process the file like normal.  However, this is disingenuous because converting hundreds of audio files one by one is going to be painful.

Any advice would be greatly appreciated.  FWIW, I tried downloading a different script and put it in /usr/share/nautilus-scripts/, made it executable, and restarted Nautilus.  None of the new scripts are showing up in nautilus-scripts-manager, which leads me to believe that perhaps the scripts directory is supposed to be something else now.  Or maybe the scripts I am trying are broken.

Help!  ](*,)

---

### Post by Scooby-2 on 2015-03-10
@[COLOR=#000000]em3raldxiii[/COLOR]

> [COLOR=#000000]Any advice would be greatly appreciated. FWIW, I tried downloading a different script and put it in /usr/share/nautilus-scripts/, made it executable, and restarted Nautilus. None of the new scripts are showing up in nautilus-scripts-manager, which leads me to believe that perhaps the scripts directory is supposed to be something else now. Or maybe the scripts I am trying are broken.[/COLOR]

FYI the correct location for your scripts is /home/user/.gnome2/nautilus-scripts/ for Nautilus. If you look there you will see a link to the audio convert program like this:
```
kevinm@G510 ~/.gnome2/nautilus-scripts $ ls -l
total 0
lrwxrwxrwx 1 kevinm kevinm 44 Mar  9 22:53 Audio files converter -> /usr/share/nautilus-scripts/ConvertAudioFile

```

If you use Caja, the location of the scripts is /home/user/.config/caja/scripts/ and, in Mint 17, you can have links here to the Nautilus scripts folder /usr/share/nautilus-scripts/.

As long as the scripts have the execute bit set, they will show up even if they don't work. When I upgraded to Mint 17 (based on Ubu 14.04) many of my scripts had to be modified as there is now a blank line added to the end of the NAUTILUS_SCRIPT_SELECTED_FILE_PATHS variable. I guess whatever is causing this is underlying, as the problem I had was that the scripts would only run on a single target file and would do nothing if more than one was selected. The audio convert program uses Zenity for file selection but I can't see with a quick glance where the file/file list is stored.

Try moving your test scripts to home/user/.gnome2/nautilus-scripts/ as you should at least see them there once they are made executable. As for Audio Convert - it hasn't been updated since 2005....

---

