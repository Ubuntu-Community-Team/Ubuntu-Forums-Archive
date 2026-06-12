---
title: "My short experience with aquaris M10"
date: 2016-04-21
forum: Mobile Technology Discussions (CLOSED)
---

### Post by bernard-godard on 2016-04-21
This is a quick review of the tablet after only a few days of usage. This is the FHD version with 1.5GHz CPU.

First thing to do is to run the system upgrade. Before performing the system upgrade, I was not able to install the document viewer from the software manager. It failed with an unhelpful error message, from what I remember it was approximately  &#8220;application failed to download or install. Try again later&#8221;. What was really frustrating is that the installer didn&#8217;t tell you how or where to get detailed information (log file?) about what exactly failed. Also there was no possibility to leave a review such as &#8220;software fails to install on Aquaris M10&#8221;, since the app store only allows you to leave reviews for installed software not the ones that failed to install. After the full system update however, the document viewer installed without a problem.


[LIST]
[*]Document viewer: it is not installed by default (see above). It works well with PDF, but does not support epub. I did not try other formats such as djvu but I have read that it supports viewing some office document formats such as odf or msdoc. It works quite nicely but is a bit slow. I think this application should be installed by default.
[*]Beru (not installed by default): ebook reader. Supports epub. Works well, but it cannot see the Documents folder in home (maybe due to appArmor profile). You have to move your document to the (obscure) location ~/.local/share/com.ubuntu.developers.rschroll.beru/Books/ . It can also import document from some web services but it does not propose using the file manager app to import document in the library.
[*]File manager app: it is not installed by default. It can access samba share. But copying files over samba is very slow and the transfer is paused whenever the focus is given to another application: basically you can do nothing when a file transfer is in progress (and you also need to set the energy settings so that the tablet never goes to sleep). Another problem I encountered is every time you try to open a document or a video, a copy of that document or video is made in the folder $HOME/Documents for documents and $HOME/Videos for Videos and this happens even in the case that the document is already in that folder, so you always get a new copy. This does not happen when you open a file directly from the Document viewer, from the gallery or videos scope. I also encountered a problem with selecting multiple files: it seems you can highlight multiple files but only one can be moved/copied at a time (the last one you selected/highlighted). Finally the external SD card is not visible by default (you have to enable full access in the app options) but this is not intuitive. I had not enabled full access originally and selecting in the file manager the sd card I only saw an empty directory and decided to make a new directory: there was no error message when creating the directory but no directory was actually created. In fact, there were already several folders in the sd card: Pictures, Movies, Documents&#8230; but they were not shown. I think it would be better if the file app was giving a permission error when trying to access the sd card if full access is not enabled otherwise this is quite confusing.
[*]Default web browser: quite good. Supports HTML5 but NOT webgl! One problem is that it fails to download zip since it doesn&#8217;t know any application that supports zip. It would be better to propose saving the file, not opening it with an application. Actually there are at least 2 apps that can extract zip: the file manager and the terminal (unzip command).
[*]Liri (web browser not installed by default): works well too, supports also html5 but not webgl.
[*]Terminal (not installed by default but should be): quite good. You can ssh into other machines. But it does not expose X. It would be much better if you could run remote graphic app via ssh -X using XMir.
[*]Tuxracer (not installed by default): Works quite well. The control have been replaced by the tablet orientation sensors. So this tablet can run OpenGL games but I remember playing this game on Debian and Mandrake Linux in 2002 so it is not a very demanding game. Actually this application doesn&#8217;t work properly anymore after the system upgrade: wrong screen orientation, image too large for screen in certain orientations as well as touch input menu layout not matching graphic menu layout in certain tablet orientations (making it very challenging to select any menu entry).
[*]Video player: works but I have many videos it cannot play (says format not supporterd). In HD videos there are often lags.
[*]External drive app: I put a new 64GB SD card in and selected format SD from the external drive app. After hours the app window was still stuck at format in pogress. Maybe this is due to the fact that the tablet was going to sleep every few minutes and  I was waking it up every about 15 minutes. In any case, I rebooted the system and actually the SD card seemed to be formatted OK with FAT FS and some folders were created: Videos, Documents.
[*]In fact it seems all apps gets paused when they are not in focus: if you launch a file move command from the terminal and switch to the web browser, the move gets paused until you switch back to the terminal.
[*]X app: Firefox, LibeOffice&#8230;: no keyboard! Acvcording to the user manual when the tablet is manually switched to desktop mode when no external keyboard is present, an on screen keyboard should appear. This doesn't work for me.
[*]Installing other legacy app: using apt-get requires to  remount the filesystem in read/write mode. I have read somewhere that this disables OTA system  updates and should not be done for the moment, but this problem will be fixed in future OTA updates. I feel like we have been cheated on this since they made quite a bit of advertisement for this feature. I hope they fix this soon.
[*]Interface: most settings are configured via sliding buttons with on/off status. The behavior of these buttons is quite erratic. I have seen many time a button switch back to its initial position a few seconds after its status was modified or the next time the window was open the button was back to it previous position. In particular it took me a very long time fighting with the interface to get the bluetooth sliding button to stay on. Whether bluetooth was actually on or not is a different matter, but just remembering the user settings seemed to be problem. I didn&#8217;t have as much problem with the other sliding buttons such as for GPS and Wifi but this was not perfect experience either.
[/LIST]

l have also experienced a case where whatever settings I chose for the duration after which no activity should trigger the system to go to sleep (10 min, 5 min, 1 min), the system was never going to sleep (even though no apps were running and the tablet was on a flat and stable surface for a long time. This was fixed after reboot.
This is it for now. Hope this can help other people. There are some good things but it is still quite far from a stable product. In particular I think the last 2 points I mentioned are unacceptable considering how the tablet was advertised.

---

### Post by Alex_Hernandez on 2016-04-25
I also have the problem with the keyboard. It does not show up in several applications. This makes the apps useless.

---

### Post by bernard-godard on 2016-04-28
In general it seems applications get paused when they are not in focus:
- file copy/move from file manager or from terminal is paused
- video playing is paused

However there some exceptions:
- audio player continues playing
- download from web browser continues in background.

This does not apply when in desktop mode. Then the applications are not paused despite not being in focus.

A few remarks about the tablet speed/reactivity:
- when moving files to the SD card while playing music from the SD card, the audio player stops (the application is still running but no audio is being played).
- often the terminal does not respond to on-screen keyboard inputs for a minute or so (could not figure out yet in which usage pattern this happens or even what makes it work again).
- tried playing a 1080p video from youtube but video+audio skips every few seconds (despite good wifi connection, same 1080p movie downloaded plays fine in video player app), same movie in 720p plays find in youtube/browser.

Also experienced video player failing on playing files from SD card and had to reboot the tablet to play the videos.

---

### Post by bryan37 on 2016-04-28
Thanks for the posts. My new aquarius m10 is limping along too. I am used to ubuntu 14, so the new operating system is very unfamiliar. I am finding that the slider buttons are not being remembered consistently. A particular annoyance is that it does not remember my wifi settings at all. They can revert within a few minutes of me correcting them, which mean whatever I was downloading at the time crashes. The Aquarius M10 is definitely not a stable product.

---

### Post by Konjad on 2016-04-28
Thanks for the heads up. I'm interested in Ubuntu phones as Android is too locked down for my taste, so I consider purchasing an Ubuntu phone in a future.

---

### Post by Mark_Daniels on 2016-05-27
Thanks, I am glad you shared your difficulties. I bought this to play an MP4 video (or converted into AVI or MKV). Only one video for an art exhibition. 23 minutes long, about 1.2 GB and needs to be looped all day and then started up again the next day. At the moment the tablet is updating a 575 MB file. How to transfer the MP4 to the table and how to play in a loop?

---

### Post by philhughes on 2016-05-27
You should be able to import books using the file manager by using the "Content Hub" - select the download icon, select Import from Content Hub, and the Browser and File Manager should appear. It does mean you end up with 2 copies of the book on the device unless you delete the original copy.

If you install the OpenStore app, there is a version of Beru on there that can read files in any directory in your home folder.

Beru is a nice app, though development seems to have come to a halt.

---

### Post by bernard-godard on 2016-06-12
I was trying to access Google drive from the tablet:
- in the default browser Google Drive interface has the same look and feel as the android app (rather than the web interface! weird) but it is incomplete: no possibility to upload files/create folders/move stuff/configure sharing... but you can browse your folders and consult documents.
- in Liri, the interface is the usual web interface as expected but it just doesn't work: no content is visible in the drive just the folder refresh animation playing forever.
- in firefox it works but you need a keyboard...

Speaking of keyboard in firefox, I have found a solution:
 [https://addons.mozilla.org/en-US/firefox/addon/fxkeyboard/](https://addons.mozilla.org/en-US/firefox/addon/fxkeyboard/)
I don't know if it has already been mention in this forum.
To install this plugin, you will probably need to temporarily connect a hardware keyboard. But then you can use firefox with this virtual keyboard (not as good as the ubuntu touch keyboard unfortunately).

Also when uploading to google drive, firefox can only see files in the home folder. It doesn't see the SD card and there is of course no option in the gtk file chooser to "unlock full access".

---

### Post by corneldardenjr on 2016-06-12
The m10 is awesome. Where is Ubuntu one cloud to hold everything together?

---

### Post by peter d on 2016-06-14
I've managed to download and upload using Google Drive. You do need to be in the Desktop view to achieve it's though (defaults to mobile view).

---

### Post by bernard-godard on 2016-06-14
Another problem with the browser keyboard (both in default browser and Liri) is that the on screen keyboard does not show in some web applications.
It does not work in Jupyter notebook [http://jupyter.org/](http://jupyter.org/) (I am running this on a server and trying to access it on my tablet).

@peter d where do you configure desktop view? Thank you.

---

