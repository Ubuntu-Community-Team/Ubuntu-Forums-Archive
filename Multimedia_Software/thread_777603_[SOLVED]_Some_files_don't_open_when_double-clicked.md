---
title: "[SOLVED] Some files don't open when double-clicked - mime problem after hardy upgrade"
date: 2008-05-01
forum: Multimedia Software
---

### Post by Tiede on 2008-05-01
Sorry my title is no clearer. I have no better way of putting this.
I have sound. That's not the problem. However, if I double-click on a music file, it doesn't open. (I've tried .wav, and .mp3 files)
If I right-click, and select the default setting (currently totem), nothing happens still.
If I right-click, go to "open with" sub-menu and click on another multimedia app, they don't open either. As if I didn't do anything.
The cursor twirls for a few seconds in all the previous cases, but that's it.
However, if I right-click and select "Open with another app" and manually type in Totem in the entry box, or if I do the same via a terminal, lo and behold, the program loads as if nothing was wrong.
Also, if I select Totem (or bmp, or rythmbox) from the menu and then within their respective gui open a file, it plays with no errors of lag time.:confused:
"previewing" the file by leaving the cursor on it works as well.
Therefore, I think my context menu is b0rked.

Any idea how I can fix this?
I first noticed this problem a day after upgrading to Hardy.
```
sudo dpkg --reconfigure -a
```didn't do squat.:(


NOTE:I don't know if this is related, but I am not getting system sounds either. made sure that login.wav is selected for login - in case it was still hard coded, as in hardy beta- but still no sounds...

Thanks in advance for any help offers/ideas.

---

### Post by Tiede on 2008-05-03
Poorly hidden bump:
```
username@machine:~$ uname -r
2.6.24-16-386

```
In case someone else was wondering...

---

### Post by cor2y on 2008-05-03
I think you hit the nail on the head on your first post.
You upgraded from an earlier version of ubuntu.
Sounds like your mime cache list may be a bit borked.
Look in ~/.local/share/applications and see what mimeapps.list mimeinfo.cache and defaults.list has for the filetypes that no longer work when double clicking.

---

### Post by Tiede on 2008-05-04
Well, I see a few entries, but I have no ieda what to do with them!
So, I'll attach them here.

If I just delete them, can I expect ubuntu to create new -and correct- ones?

---

### Post by Tiede on 2008-05-05
I am no expert, and can't understand what is going on with the entries in these files.
BUt something odd caught my attention. Some entries are listed twice -or even more times than that, in the folder. Anyone knows what that is all about. This output should explain what I am seeing:

```
tiede@Laptop:~$ ls /home/tiede/.local/share/applications/
abuse.desktop
anagramarama.desktop
audacity-usercreated.desktop
bmp.desktop
cddb-slave.desktop
codeblocks.desktop
codeblocks-usercustom.desktop
dvdrip-usercreated.desktop
easytag-usercustom.desktop
firefox-usercustom.desktop
firefox-usercustom-usercustom.desktop
flight-of-the-amazon-queen.desktop
f-spot-view.desktop
gconf-editor.desktop
gdmsetup.desktop
gedit-usercustom-1.desktop
gedit-usercustom-2.desktop
gedit-usercustom.desktop
gimp-2.2-usercustom.desktop
gnome-keyring-manager.desktop
gnome-terminal-usercustom.desktop
hplip.desktop
hwdb.desktop
inkscape-usercustom.desktop
kcontrol.desktop
kde-lynx.desktop
mimeapps.list~
nautilus-file-management-properties.desktop
nvu-usercreated.desktop
ooo-writer.desktop
picasa-usercreated.desktop
pidgin.desktop
screensavers-pacman.desktop
sound-juicer.desktop
supertux.desktop
time.desktop
timidity-interfaces-extra.desktop
timidity-usercreated.desktop
totem.desktop
userapp-totem-ANFDAU.desktop
userapp-totem-H5BAAU.desktop
userapp-totem-IRV99T.desktop
userapp-totem-PWCKAU.desktop
USP Configuration-1.desktop
USP Configuration-2.desktop
USP Configuration-3.desktop
USP Configuration-4.desktop
USP Configuration.desktop
vlc.desktop
vlc-usercustom.desktop
wine-regedit.desktop
wine-usercreated.desktop
wine-winecfg.desktop
X-Debian-Apps-Editors-openoffice.org_writer-usercustom.desktop
X-Debian-Apps-Net-firefox_web_browser-usercustom.desktop
X-Debian-XShells-gnome_terminal-usercustom.desktop
tiede@Laptop:~$ 
```

---

### Post by Tiede on 2008-05-07
I wonder how many times I can legally bump this...

---

### Post by Tiede on 2008-05-07
I thought I had an idea, and decided to move my mimeapps.list, mimeinfo.list and defaults.list out of that folder, so the system can try and do them again. Well, ubuntu recreated the file mimeapps.list, but the behavior is still there.
I am stomped. Any ideas how to fix this, anyone? I wanted to file a bug, but since I am the only one seeing this, I haven't done so...
This is getting a little irritating...

---

### Post by theboatashore on 2008-05-08
I have the same problem but for me it's for all mimetypes except images.  Double clicking on files, either on the desktop or within folders doesn't do anything.  Neither does "Open with..."

---

### Post by Tiede on 2008-05-09
I am starting to think that it will be different filetypes on different filesystems, maybe depending on which entry the user "custom-opened" before. For example, have you ever edited the default application that is supposed to open images? Maybe that's why it opens. If I select an audio file (say .ogg) and select Open with, then within the browser, type *totem*, then .ogg files suddenly open correctly whenever i click on them. Other audio files will still behave oddly, but oggs won't anymore.
So a workaround to the problem might be to manually set ALL the awkward behaving file extension to open with a prefered application.

ToDo:
[LIST=1]
[*] Check if other filetypes are affected by this bug under my system setup.
[*] Find out what package is responsible for handling mimetypes in ubuntu.
[*] File a launchpad bug report against that package.
[*] Test whether the culprit package (or packages if necessary) can be fixed with dpkg-reconfigure.
[*] Search possible fixes as they come and if all else fails, manually set open action for each file to a known application that handles that type of file.
[/LIST]

---

### Post by Tiede on 2008-05-12
Is anyone else even *having* this issue. I really would like to know. It's driving me **insane**!

---

### Post by Tiede on 2008-05-20
Well, if anyone else has this problem, I am posting what I did to get it to work (since apparently, no one else has a better solution)

Since my mime was b0rked, I decided to delete the folder ~/.local/share from my PC.
the exact code is ```
rm -R ~/.local/share
```
**[color=red]ATTENTION!!![/color]The above code contains the [color=green]rm[/color] bit of code and should not be run unless you know what you are doing.**
It is put here for clarity's sake only, if you need to delete the mentioned folder, I advise using nautilus, browsing to your ~/.local and delete the folder share from there.
[color=red]You've been warned![/color]

---

