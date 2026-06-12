---
title: "How to run GIMP AppImage"
date: 2023-01-31
forum: Multimedia Software
---

### Post by satimis on 2023-01-31
Hi all,

Ubuntu 22.04

I have gimp-mathmap-22-04jammy.AppImage in my data which was downloaded on Jun 2022.  But I couldn't execute it.  Right-click it -> Run without response.

Properties -> Permission
Execute [check] Allow executing file as program (already done)

Also on Terminal;
$ sudo chmod +x gimp-mathmap-22-04jammy.AppImage 
without result

Then I download another GIMP AppImages on
[https://github.com/aferrero2707/gimp-appimage/releases/tag/continuous](https://github.com/aferrero2707/gimp-appimage/releases/tag/continuous)

GIMP_AppImage-release-2.10.22-x86_64.AppImage
and
GIMP_AppImage-git-2.10.25-20210527-x86_64.AppImage

The same situation.  I couldn't start them.

But on Terminal run;
$ ps aux | grep -i appimage```

satimis    40463  0.0  0.0  17864  2236 pts/2    S+   17:21   0:00 grep --color=auto -i appimage

```


Please help.  Thanks

Regards

---

### Post by Dennis N on 2023-01-31
Try to run it from the terminal to see if there is an error message. It can reveal why it does not run. I discovered that one of my AppImages failed to start because there was a missing library. Once I installed that from the Ubuntu repository, it began to work. Lesson learned: AppImages don't always come with ALL the libraries they need. They rely on some NOT in the AppImage package.

---

### Post by satimis on 2023-01-31
> **Dennis N said:**
> Try to run it from the terminal to see if there is an error message. It can reveal why it does not run. I discovered that one of my AppImages failed to start because there was a missing library. Once I installed that from the Ubuntu repository, it began to work. Lesson learned: AppImages don't always come with ALL the libraries they need. They rely on some NOT in the AppImage package.
Hi,

Thanks for your advice.

I have following 3 AppImages download;
1) gimp-mathmap-22-04jammy.AppImage
2) GIMP_AppImage-release-2.10.22-x86_64.AppImage
3) GIMP_AppImage-git-2.10.25-20210527-x86_64.AppImage 

$ ./gimp-mathmap-22-04jammy.AppImage```
 
dlopen(): error loading libfuse.so.2

AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See https://github.com/AppImage/AppImageKit/wiki/FUSE 
for more information

```

Other 2 AppImages with the same error

$ apt policy fuse```

fuse:
  Installed: (none)
  Candidate: 2.9.9-5ubuntu3
  Version table:
     2.9.9-5ubuntu3 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

$ sudo apt install fuse

Then run again;


$ ./gimp-mathmap-22-04jammy.AppImage```
 
mount: /var: wrong fs type, bad option, bad superblock on overlay-var, missing codepage or helper program, or other error.
/tmp/.mount_gimp-meCMRWp/shradiko: 33: gimp: not found

```

$ ./GIMP_AppImage-git-2.10.25-20210527-x86_64.AppImage 
...
GIMP 2.10 starts

$ ./GIMP_AppImage-release-2.10.22-x86_64.AppImage
Also GIMP 2.10 starts

Which package shall I use, 2) or 3) ?  Thanks

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Furthermore kindly advise how to install the AppImage with its icon on the menu.  So that I can click the icon to start GIMP.  I have done it before.  Sorry I forgot the steps.

I'll download its icon on Internet.

Regards

---

### Post by Dennis N on 2023-01-31
I would use GIMP_AppImage-release-2.10.22-x86_64.AppImage. 
You don't need two - I would delete the other one.

You want it to show up with the other applications and be found by the overview search, so it needs a desktop file in order to appear. Here's the one I use for LibreOffice:

```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=/home/dmn/.local/share/icons/libreoffice-appimage.svg
Type=Application
Categories=Office;
Exec=/home/dmn/appimages/LibreOffice-6.1.5-x86_64.AppImage --writer %U
MimeType=application/vnd.oasis.opendocument.text;
Name=Writer AppImage
GenericName=Word Processor
StartupWMClass=libreoffice
StartupNotify=true
#X-GIO-NoFuse=true

```

This desktop file is in ~/.local/share/applications, but you could put it in /usr/share/applications. In mine, I only use the Writer, so I added --writer to the filename. Also, in case you notice, this is not the newest version - I didn't want that. Why? 6.1.x is the last L.O. series to still use Firefox Personas for theming. The icon is custom.

---

### Post by satimis on 2023-01-31
> **Dennis N said:**
> I would use GIMP_AppImage-release-2.10.22-x86_64.AppImage. 
You don't need two - I would delete the other one.

No, I only need 1 AppImage.  I'll delete the other 2 as advised.  Thanks

> 
You want it to show up with the other applications and be found by the overview search, so it needs a desktop file in order to appear. Here's the one I use for LibreOffice:

```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=/home/dmn/.local/share/icons/libreoffice-appimage.svg
Type=Application
Categories=Office;
Exec=/home/dmn/appimages/LibreOffice-6.1.5-x86_64.AppImage --writer %U
MimeType=application/vnd.oasis.opendocument.text;
Name=Writer AppImage
GenericName=Word Processor
StartupWMClass=libreoffice
StartupNotify=true
#X-GIO-NoFuse=true

```

This desktop file is in ~/.local/share/applications, but you could put it in /usr/share/applications. In mine, I only use the Writer, so I added --writer to the filename. Also, in case you notice, this is not the newest version - I didn't want that. Why? 6.1.x is the last L.O. series to still use Firefox Personas for theming. The icon is custom.
I want its icon displayed on the left vertical menu.  I have done this setting for other AppImages before.  Unfortunate I forgot the steps to make it.  I don't know whether I can find the document on my database.

Please refer to the screenshot of the left vertical menu bar.

Regards

---

### Post by Dennis N on 2023-01-31
> I want its icon displayed on the left vertical menu. I have done this setting for other AppImages before. Unfortunate I forgot the steps to make it. I don't know whether I can find the document on my database.

All you need is to make a .desktop file for the AppImage. Then it's icon will appear on the dock when started, and you can add it to favorites to keep it there.

---

### Post by satimis on 2023-02-01
> **Dennis N said:**
> All you need is to make a .desktop file for the AppImage. Then it's icon will appear on the dock when started, and you can add it to favorites to keep it there.
/home/satimis/Video/GIMP_AppImage-release-2.10.22-x86_64.AppImage. 
/home/satimis/Picture/gimpicon.jpeg
.local/share/applications/gimp.desktop

Please advise how to start GIMP ?

Start gimp.desktop on Terminal?

Thanks

Regards

---

### Post by satimis on 2023-02-02
Hi Dennis,

I couldn't finish installing GIMP on its AppImage.  I couldn't run gimp.desktop on Terminal to start GIMP.  If starting GIMP AppImage on Terminal, I couldn't add its icon to favorite.  Besides the icon is not the icon download on Internet.

Unfortunately I couldn't find the document installing the application on its AppImage in the past.  Fortunately I found Avidemux and Shotcut installed on a SSD running Ubuntu 22.04, also on their AppImage.

Their desktop files are on .local/share/application/

$ cat .local/share/applications/shotcut.desktop```
 
[Desktop Entry]
Name=shotcut
Type=Application
Exec=/home/satimis/Videos/shotcut-linux-x86_64-220130.AppImage
Icon=/home/satimis/Pictures/shotcut.png
Categories=Graphics;Viewer;

```

$ cat .local/share/applications/avidemux.desktop ```

[Desktop Entry]
Name=avidemux
Type=Application
Exec=/home/satimis/Videos/avidemux_2.8.0.appImage
Icon=/home/satimis/Pictures/avidemux.jpg

```

Their icons were download on Internet, not in the application.

Have you had any idea ?

Thanks

Regards

---

### Post by Dennis N on 2023-02-02
The GIMP AppImage works fine for me when run from terminal. The appimage I located was on the appimage hub. The Gimp downloads page does not offer an appimage for Linux - it recommends Flatpak or the Ubuntu repository version. I personally would use the Flatpak.

If you want to continue with an AppImage,

1) Did you make the downloaded file executable? Otherwise, nothing will happen.
2) command to run from terminal:
```
dmn@Tyana-vm:~/Downloads$ ./GIMP_AppImage-git-2.10.21-20201001-x86_64.AppImage
``` 
There are tons of output as it loads. While loading, it also asked if I wanted to integrate with the system by adding an entry to the applications menu and provide an icon. If you plan to keep it, this looks like a good option.

---

### Post by satimis on 2023-02-02
> **Dennis N said:**
> The GIMP AppImage works fine for me when run from terminal. The appimage I located was on the appimage hub. The Gimp downloads page does not offer an appimage for Linux - it recommends Flatpak. I personally would use the Flatpak.

If you want to continue with an AppImage,

1) Did you make the downloaded file executable? Otherwise, nothing will happen.
2) command to run from terminal:
```
dmn@Tyana-vm:~/Downloads$ ./GIMP_AppImage-git-2.10.21-20201001-x86_64.AppImage
``` 
There are tons of output as it loads. While loading, it also asked if I wanted to integrate with the system by adding an entry to the applications menu and provide an icon. If you plan to keep it, this looks like a good option.
Hi,

Thanks for your reply.

GIMP_AppImage-release-2.10.22-x86_64.AppImage, which you suggested me to work on, is executable .  I can start it on Terminal without problem but I can't add its icon to Favorite.  Besides its icon is NOT the same icon which I download on Internet and add it to /home/satimis/Picture/gimpicon.jpeg

I have done installing AppImage, adding its icon to Favorite, in the past several times.  The steps were not complicate.  Unfortunately I forgot the steps.  I have been searching on Internet but without result.

Regards

---

### Post by Dennis N on 2023-02-02
>  Besides its icon is NOT the same icon which I download on Internet and add it to /home/satimis/Picture/gimpicon.jpeg

Could the file type make a difference? The application icons nowadays are seem always to be .svg or .png files. There are lots of gimp icons in google image search - .png or .svg. Try using a .svg or .png icon. If I want a custom icon, it's going to be .svg. I use Inkscape for making that.

---

### Post by satimis on 2023-02-02
> **Dennis N said:**
> Could the file type make a difference? The application icons nowadays are seem always to be .svg or .png files. There are lots of gimp icons in google image search - .png or .svg. Try using a .svg or .png icon. If I want a custom icon, it's going to be .svg. I use Inkscape for making that.
Tried gimpicon.png without result

Steps performed;
1. On Terminal run "Convert" to convert gimpicon.jpeg to gimpicon.png
2. sudo nano .local/share/applications/gimp.desktop
Change:
Icon=/home/satimis/Pictures/gimpicon.jpeg
To:
Icon=/home/satimis/Pictures/gimpicon.png

On Terminal, start GIMP_AppImage-release-2.10.22-x86_64.AppImage
No change on icon - still not gimpicon.png

Pls refer to my posting #8 above
.local/share/applications/avidemux.desktop```
 
Icon=/home/satimis/Pictures/avidemux.jpg

```
.jpg works without problem

I suppose it needs to run gimp.desktop to start GIMP_AppImage-release-2.10.22-x86_64.AppImage ?

Regards

---

### Post by Dennis N on 2023-02-02
To change your icon to a different type, you would need to convert it. Image viewer will do that. Load it and save as a different file type. But, as you say, the file type doesn't seem to be the problem if the other .jpg images are ok. So the reason is unclear.

Another way to manage AppImages is to use **AppImage Lauhcher**. It is described here:
[https://www.omgubuntu.co.uk/2022/10/appimagelauncher-install-on-ubuntu](https://www.omgubuntu.co.uk/2022/10/appimagelauncher-install-on-ubuntu)
You might want to check it out. I have not tried it myself.

---

### Post by satimis on 2023-02-02
> **Dennis N said:**
> To change your icon to a different type, you would need to convert it. Image viewer will do that. Load it and save as a different file type. But, as you say, the file type doesn't seem to be the problem if the other .jpg images are ok. So the reason is unclear.

Another way to manage AppImages is to use **AppImage Lauhcher**. It is described here:
[https://www.omgubuntu.co.uk/2022/10/appimagelauncher-install-on-ubuntu](https://www.omgubuntu.co.uk/2022/10/appimagelauncher-install-on-ubuntu)
You might want to check it out. I have not tried it myself.
Hi,

Thanks for your link.  I'll go through it.

However according to my recollection it should not be so difficult.

I have both AvideMux and ShotCut running here.  They were installed on AppImage.  Unfortunately I couldn't find their installation file on the database of my computer.

I'll come back later.

Regards

---

### Post by satimis on 2023-02-03
Hi Dennis N,

 Problem solved as follow;
 Remark: GIMP AppImage is installed on Ubuntu 22.04 VM
 
 On Terminal of Ubuntu 22.04 VM
 $ ls -al Pictures/gimpicon.png ```

-rwxrwx--- 1 root vboxsf 62571 Feb  3 00:11 Pictures/gimpicon.png

```

Then run;
$ sudo chown satimis:vboxsf Pictures/gimpicon.png

-> Activities
GIMP icon, gimpicon.png, download on Internet is there

right-click it -> add to Favorites

The icon is then added to the dock/left vertical menu

Clicking this icon starts GIMP 2.10

The solution is very simple but it takes me 2 days to find it.

Regards

---

