---
title: "Rhythmbox cannot be set as music default player"
date: 2021-05-01
forum: Multimedia Software
---

### Post by hari-seldon2 on 2021-05-01
When I double-click on music files (mp3, m4a) Ubuntu opens them with Video not Rhythmbox.  When I open with Files and right-click and select Rhythmbox then it does open the music with Rhythmbox, but I want to fix it so it opens with Rhythmbox on a double-click.

TL : DR why does "audio/m4a=org.gnome.Totem.desktop" and "audio/m4a=org.gnome.Totem.desktop;rhythmbox.desktop;" not work (open Video not Rhythmbox) but "audio/m4a=rhythmbox.desktop;" does work why is GNOME failing?  Is having both GNOME File Manager and Nautilus File Manager the problem?

My Settings -> Default Applications has Video to play videos and Rhythmbox to play music, but that does not match what the Nautilus File Manager when I right-click a music file the File Manager says that Video is the default music player and when I click "Set as default" Rhythmbox nothing happens.  When I click "Reset to system defaults" it keeps Video as the default music player and does not sync up with Settings -> Default Applications that has Video to play videos and Rhythmbox to play music.

When I use the GNOME File Manager (replacement to Nautilus) and right-click on the music file I can right click the Video and can sometimes make it forget to use Video to play that music file type and when I double-click the music file it still opens in Video.  I can get GNOME File Manager to play Rhythmbox by right-clicking and selecting Rhythmbox but it does not remember that choice when I double-click.

I am pretty sure the problem is my mimeapps.list is wrong (see attached mimeapps.list.txt for the full list), I used to have VLC player installed so maybe video/mp4=vlc_vlc.desktop; is wrong and that confuses my computer?  Or maybe a hard fix could be to replace "org.gnome.Totem.desktop" with "rhythmbox.desktop" since GNOME is failing.
video/mp4=vlc_vlc.desktop;
audio/x-mp3=org.gnome.Totem.desktop;rhythmbox.desktop;
audio/m4a=org.gnome.Totem.desktop
audio/x-m4a=org.gnome.Totem.desktop
audio/mp4=rhythmbox.desktop

So please tell me how to fix my mimeapps.list

I have both GNOME file manager and Nautilus File Manager because I can only create Ubuntu .DESKTOP url files from Nautilus.

I have a special patch on my ASUS G752VL Ubuntu 20.04.2 LTS because that's the only way to get it to not play audio on the speakers and instead play it on my headphones.  See the link below for the patch I found for a similar laptop ASUS G752VY
[https://askubuntu.com/questions/1165048/asus-rog-g752vt-alsa-configuration](https://askubuntu.com/questions/1165048/asus-rog-g752vt-alsa-configuration)
From that I did this:
adding file /lib/firmware/asus-g752vl.fw

adding this to the end of alsa-base.conf: options snd-hda-intel enable=1 index=0 enable_msi=1 model=asus-mode5 patch=asus-g752vl.fw

I also have a special runurl and mswinurl.desktop from [https://devio.wordpress.com/2020/03/22/opening-url-files-in-ubuntu/](https://devio.wordpress.com/2020/03/22/opening-url-files-in-ubuntu/) that lets me open Windows URL files in Ubuntu and send their URL to make a Firefox tab
mswinurl.desktop was the sixth file so I could not attach it so I put its contents here:
[Desktop Entry]
Name=Firefox Shortcut
GenericName=Firefox Shortcut

Type=Application
Exec=runurl %U
TryExec=firefox
MimeType=application/x-mswinurl;
Icon=firefox

I also have a special logind.conf file that makes sure that when I close the lid on my laptop it does not suspend it shuts down Ubuntu, because Suspend is bugged on my laptop it does suspend and unsuspend but the backlight for my LED screen does not turn back on until I reboot and I have to shine a flashlight to see well enough to click around to shut down Ubuntu
HandleLidSwitch=poweroff
HandleLidSwitchExternalPower=poweroff

---

### Post by Xian on 2021-05-01
Let's try a 2-step approach:

In a terminal navigate to a folder w/MP3 file. 

What is the output of the command below?
If 1) is not Rhythmbox then select the desired option number.

$ mimeopen -d <file_name>.mp3

Run the command again.
Verify that Rhythmbox is now the 1st option. 

Next in Files/Nautilus right-click the MP3 file -> Properties -> Open With tab.
Verify that the default is set to Rhythmbox.

Any change?

---

### Post by hari-seldon2 on 2021-05-03
TL : DR I did all that and the commands seemed to set Rhythmbox as default but then did Properties -> Open With Tab and still cannot change the default from Videos to Rhythmbox.  When I double-click it still opens in Videos.  Is me having both GNOME and Nautilus the problem?  Is my mimeapps.list wrong?  As I said if I change the mp3 and m4a parts of mimeapps.list from going to GNOME to going to Rhythmbox then that works I double-click and it goes to Rhythmbox.  But I don't prefer that rough solution because it might take agency away from my Settings -> Default Applications by skipping GNOME and going right to Rhythmbox.

Is there a way to change it from "Rhythmbox  (rhythmbox)" to "Rhythmbox (org.gnome.Totem)"?  Would that be a fix?

thomas@thomas-G752VL:~/Music/Test$ mimeopen -d BTA.mp3
Please choose a default application for files of type audio/mpeg

    1) Videos  (org.gnome.Totem)
    2) Rhythmbox  (rhythmbox)
    3) KeePassXC  (keepassxc_keepassxc)
    4) clamtk  (clamtk-kde)
    5) Share with Skype  (skype_skypeforlinux-share)
    6) Other...

use application #2
Opening "BTA.mp3" with Rhythmbox  (audio/mpeg)

(rhythmbox:4799): Gtk-WARNING **: 13:24:55.095: actionhelper: action app.play-repeat can't be activated due to parameter type mismatch (parameter type NULL, target type b)

(rhythmbox:4799): Gtk-WARNING **: 13:24:55.095: actionhelper: action app.play-shuffle can't be activated due to parameter type mismatch (parameter type NULL, target type b)
^C
thomas@thomas-G752VL:~/Music/Test$ mimeopen -d BTA.mp3
Please choose a default application for files of type audio/mpeg

    1) Rhythmbox  (rhythmbox)
    2) Videos  (org.gnome.Totem)
    3) KeePassXC  (keepassxc_keepassxc)
    4) clamtk  (clamtk-kde)
    5) Share with Skype  (skype_skypeforlinux-share)
    6) Other...

use application #1
Opening "BTA.mp3" with Rhythmbox  (audio/mpeg)

(rhythmbox:4838): Gtk-WARNING **: 13:25:35.296: actionhelper: action app.play-repeat can't be activated due to parameter type mismatch (parameter type NULL, target type b)

(rhythmbox:4838): Gtk-WARNING **: 13:25:35.296: actionhelper: action app.play-shuffle can't be activated due to parameter type mismatch (parameter type NULL, target type b)
/usr/lib/python3/dist-packages/gi/overrides/GObject.py:502: Warning: ../../../gobject/gsignal.c:2736: instance '0x55a59e9d6540' has no handler with id '14323'
  return func(*args, **kwargs)
/usr/lib/python3/dist-packages/gi/overrides/GObject.py:502: Warning: ../../../gobject/gsignal.c:2736: instance '0x55a59e9d6540' has no handler with id '14322'
  return func(*args, **kwargs)

(rhythmbox:4838): Gtk-WARNING **: 13:25:39.051: Can't set a parent on widget which has a parent
thomas@thomas-G752VL:~/Music/Test$ mimeopen -d BTA.mp3
Please choose a default application for files of type audio/mpeg

    1) Rhythmbox  (rhythmbox)
    2) Videos  (org.gnome.Totem)
    3) KeePassXC  (keepassxc_keepassxc)
    4) clamtk  (clamtk-kde)
    5) Share with Skype  (skype_skypeforlinux-share)
    6) Other...

use application #1
Opening "BTA.mp3" with Rhythmbox  (audio/mpeg)

(rhythmbox:4975): Gtk-WARNING **: 13:25:46.492: actionhelper: action app.play-repeat can't be activated due to parameter type mismatch (parameter type NULL, target type b)

(rhythmbox:4975): Gtk-WARNING **: 13:25:46.492: actionhelper: action app.play-shuffle can't be activated due to parameter type mismatch (parameter type NULL, target type b)
/usr/lib/python3/dist-packages/gi/overrides/GObject.py:502: Warning: ../../../gobject/gsignal.c:2736: instance '0x55cba6c2e100' has no handler with id '14324'
  return func(*args, **kwargs)
/usr/lib/python3/dist-packages/gi/overrides/GObject.py:502: Warning: ../../../gobject/gsignal.c:2736: instance '0x55cba6c2e100' has no handler with id '14323'
  return func(*args, **kwargs)

(rhythmbox:4975): Gtk-WARNING **: 13:25:48.821: Can't set a parent on widget which has a parent
thomas@thomas-G752VL:~/Music/Test$ 

MP3 file -> Properties -> Open With Tab shows Videos as default and I click Set as default Rhythmbox and that does not do anything.

---

### Post by hari-seldon2 on 2021-10-02
SOLUTION: take out the big hammer on mimeapps.list
CHANGE:
audio/m4a=org.gnome.Totem.desktop
audio/mp3=org.gnome.Totem.desktop
TO:
audio/m4a=rhythmbox.desktop
audio/mp3=rhythmbox.desktop

That big hammer forces double-click to open m4a and mp3 and not Videos anymore.

Any other audio formats you can do that conversion too those were just the two common ones I have.

Settings says Rhythmbox is the default muisc player before and after this fix.  I don't know of any way to get Settings to work again and stop audio files opening in Videos.  So I had to use the big hammer.

---

