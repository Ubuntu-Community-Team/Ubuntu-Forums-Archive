---
title: "How to restore color and sharpness of old photos"
date: 2024-10-31
forum: Multimedia Software
---

### Post by satimis on 2024-10-31
Hi all

Please advise how to restore old color photos.

I have old color hardcopy photos converted to digital copies using an android phone connected via an USB cable to Ubuntu 24.04 desktop PC with remote desktop.  This setup works for me without problem.  Copies of 3 digitized photos are attached here as example.

I expect to retouch them adding colors on the fade colored photos as well as making the photos more sharp .  Please advice.

I'll not print the edited photos but using them building digital slideshow only.

Thanks in advance.

Regards

---

### Post by Dennis N on 2024-11-01
I use a program named **Upscayl**. It's one of my favorite programs.

> *Upscayl is a powerful image upscaling tool that uses advanced AI technology to enhance your images.*
It not for editing colors.

Learn more:
Webpage:
[https://upscayl.org/](https://upscayl.org/)

It's available as a Flatpak.

---

### Post by satimis on 2024-11-01
> **Dennis N said:**
> I use a program named **Upscayl**. It's one of my favorite programs.


It not for editing colors.

Learn more:
Webpage:
[https://upscayl.org/](https://upscayl.org/)

It's available as a Flatpak.
Hi Dennis N,

Thanks for your advice.

There are websites offer FREE online sharpening photo service, using AI technology.  I use their service frequently but the color of the photo gone.  Please refers to attached screenshots, before and after editing.  The blue sky was added by me, also using FREE online service.

Regards

---

### Post by Dennis N on 2024-11-01
Personally, I don't want to send my images to someone else to process. Its a privacy thing.
I'm wondering, do you get options for an AI model to use with the online method? Upscayl has 6 models. You can get different results depending on the model used.

---

### Post by Dennis N on 2024-11-01
I tried your original image in Upscayl and I think I can get a much better result. Using Fast Real-Esrgan. You should try it out.

For corrections to contrast, gamma, saturation, color balancing etc. I use gthumb. Easy.

---

### Post by satimis on 2024-11-01
> **Dennis N said:**
> Personally, I don't want to send my images to someone else to process. Its a privacy thing.
I'm wondering, do you get options for an AI model to use with the online method? Upscayl has 6 models. You can get different results depending on the model used.
They are auto-proceeded after you selecting the option.

---

### Post by satimis on 2024-11-01
> **Dennis N said:**
> I tried your original image in Upscayl and I think I can get a much better result. Using Fast Real-Esrgan. You should try it out.

For corrections to contrast, gamma, saturation, color balancing etc. I use gthumb. Easy.
Hi Dennis N,

I'll install and test Upscayl on Ubuntu 22.04.  I don't know whether it works here.

OpenShot and GIMP (both REPO and Snap versions) are unable to work properly on both Ubuntu 22.04 and 24.04 on my daily working PC, this PC.  I suspect whether it is the problem of this PC.  That is why I'm planning to build a new PC.

I have 2 drives on this PC, one running Ubuntu 24.04 and another Ubuntu 22.04.  Anyway I'll test Upscayl on Ubuntu 22.04.

Whether following online document is suitable for me to install Upscayl ?

Enable snaps on Ubuntu and install Upscayl
[https://snapcraft.io/install/upscayl/ubuntu](https://snapcraft.io/install/upscayl/ubuntu)

[B][COLOR="#FF0000"]Edit
===[/COLOR][/B]
Could you please post the edited image here?  Thanks

Regards

---

### Post by Dennis N on 2024-11-01
I installed Upscayl as a Flatpak. Works great. 

```
[dmn@Sydney ~]$ flatpak search Upscayl
Name            Description                                    Application ID             Version        Branch        Remotes
Upscayl         Free and Open Source AI Image Upscaler         org.upscayl.Upscayl        2.11.5         stable        flathub

```

For your image, I used Fast Real-Esrgan and 2x scaling. I would have attached it, but the file size and dimensions are too large for the forum.

---

### Post by satimis on 2024-11-01
> **Dennis N said:**
> I installed Upscayl as a Flatpak. Works great. 


```
[dmn@Sydney ~]$ flatpak search Upscayl
Name            Description                                    Application ID             Version        Branch        Remotes
Upscayl         Free and Open Source AI Image Upscaler         org.upscayl.Upscayl        2.11.5         stable        flathub

```

For your image, I used Fast Real-Esrgan and 2x scaling. I would have attached it, but the file size and dimensions are too large for the forum.
Hi Dennis N,

Performed following steps:-

$ flatpak search Upscayl```

Name   Description                     Application ID     Version Branch Remotes
Upsca… Free and Open Source AI Image … …g.upscayl.Upscayl 2.11.5  stable flathub

```

$ flatpak install flathub org.upscayl.Upscayl```

....
.....
Installation complete.

```

It went through without complaint untill finish

$ upscayl```

Command 'upscayl' not found, but can be installed with:
sudo snap install upscayl

```

$ Upscayl```

Command 'Upscayl' not found, did you mean:
  command 'upscayl' from snap upscayl (2.11.5)
See 'snap info <snapname>' for additional versions.

```

Unable to start Upscayl

Regards

---

### Post by Dennis N on 2024-11-02
Flatpaks will put an icon in the Applications menu, or search for Upscayl from the overview screen. So you launch it like any other application.

If you really want to start it from the terminal, you have to use the flatpak command with the run option and the application id, not the program name. Not the best way. Like this:

flatpak run org.upscayl.Upscayl

(If run this terminal command on my system, I get numerous irrelevant system messages in the terminal. But it starts.)

---

### Post by satimis on 2024-11-02
> **Dennis N said:**
> Flatpaks will put an icon in the Applications menu, .......

Sorry no.

I found Upscayl on the top bar "Type to search" and add its icon on the left vertical bar, Menu Bar.  But it can't start by clicking its icon.  It is very strange to me!!!  It is the same after rebooting the PC.

Regards

---

### Post by Dennis N on 2024-11-02
> **satimis said:**
> Sorry no.

I found Upscayl on the top bar "Type to search" and add its icon on the left vertical bar, Menu Bar.  But it can't start by clicking its icon.  It is very strange to me!!!  It is the same after rebooting the PC.

Regards
Clearly something is wrong somewhere. But it does start from the terminal so you can still try it? I'm interested in hearing what you think of the results it produces.
 
Do other Flatpaks launch normally? (from an icon).
If Upscayl is the only Flatpak you have, I suggest installing another one to see if the problem exists there too. It's up to you, but woth checking. If you want a suggestion for one, a small and simple app like **Blanket** might serve as a test. It plays ambient background sounds. You can uninstall after testing.

```
flatpak install flathub com.rafaelmardojai.Blanket
```


Note that sudo is **not** used when installing Flatpaks.

---

### Post by 1fallen on 2024-11-02
I remember this when I last looked at Gnome, the first install of flatpak needed to restart the session then things behaved as expected.

Then I ran it as:
```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=upscayl-run --file-forwarding org.upscayl.Upscayl @@u %U @@


```
without a session restart, Dennis N already installed flatpakk so it just works for him.

---

### Post by satimis on 2024-11-02
> **1fallen2 said:**
> I remember this when I last looked at Gnome, the first install of flatpak needed to restart the session then things behaved as expected.

Then I ran it as:
```
/usr/bin/flatpak run --branch=stable --arch=x86_64 --command=upscayl-run --file-forwarding org.upscayl.Upscayl @@u %U @@


```
without a session restart, Dennis N already installed flatpakk so it just works for him.
Hi 1fallen2,

Thanks for your advice.

Run your command on Terminal:
$ /usr/bin/flatpak run --branch=stable --arch=x86_64 --command=upscayl-run --file-forwarding org.upscayl.Upscayl @@u %U @@
```

...
...
.....
[3:1103/093556.173190:ERROR:leveldb_factory.cc(88)] Failed to open LevelDB database from /home/satimis/.var/app/org.upscayl.Upscayl/config/Upscayl/IndexedDB/file__0.indexeddb.leveldb,IO error: /home/satimis/.var/app/org.upscayl.Upscayl/config/Upscayl/IndexedDB/file__0.indexeddb.leveldb/LOCK: File currently in use. (ChromeMethodBFE: 15::LockFile::2)
09:35:56.556 › &#9881;&#65039; Setting saveImageAs to png
09:35:56.557 › &#128256; Setting model to realesrgan-x4plus
09:35:56.558 › &#9881;&#65039; Setting gpuId to empty string
09:35:56.559 › &#128256; Setting model to null
09:35:56.562 › &#128256; Setting model to realesrgan-x4plus
Warning: vkCreateInstance: Found no drivers!
Warning: vkCreateInstance failed with VK_ERROR_INCOMPATIBLE_DRIVER
    at CheckVkSuccessImpl (../../third_party/dawn/src/dawn/native/vulkan/VulkanError.cpp:88)
    at CreateVkInstance (../../third_party/dawn/src/dawn/native/vulkan/BackendVk.cpp:458)
    at Initialize (../../third_party/dawn/src/dawn/native/vulkan/BackendVk.cpp:344)
    at Create (../../third_party/dawn/src/dawn/native/vulkan/BackendVk.cpp:266)
    at operator() (../../third_party/dawn/src/dawn/native/vulkan/BackendVk.cpp:521)



```
hanging there.

Still can't find Upscayl window on display.

Right-click Upscayl icon on Menu Bar.  It shows```

All windows
New window
Remove from Favorites
Show details
Quit

```

Clicking "All windows" and "New window" without response

Clicking "Show details" please refers to the screenshots attached.

Regards

---

### Post by Dennis N on 2024-11-03
_**For Reference:**_

[**Using Flatpak (documentation)**]("https://docs.flatpak.org/en/latest/using-flatpak.html")

in particular, see the section:
> Running applications
Once an application has been installed, it can be launched using the run command and its application ID:
$ flatpak run org.gimp.GIMP

Remember that Flatpaks are universal applications, so there must be a universal way to run them in any environment. Using a terminal is how. With our Gnome systems, we have menus, docks, searching, and the Application Matrix (or Grid) as additional ways to launch.

---

### Post by satimis on 2024-11-03
> **Dennis N said:**
> _**For Reference:**_

[**Using Flatpak (documentation)**]("https://docs.flatpak.org/en/latest/using-flatpak.html")

in particular, see the section:

Remember that Flatpaks are universal applications, so there must be a universal way to run them in any environment. Using a terminal is how. With our Gnome systems, we have menus, docks, searching, and the Application Matrix (or Grid) as additional ways to launch.
Hi Dennis N,

Perform following steps;

$ cd /.var/app/

$ ls```

org.inkscape.Inkscape  org.upscayl.Upscayl
org.openshot.OpenShot  org.videolan.VLC

```

$ flatpak run org.upscayl.Upscayl```

....
.....
......
23:18:18.708 › &#9881;&#65039; Setting saveImageAs to png
23:18:18.710 › &#128256; Setting model to realesrgan-x4plus
23:18:18.711 › &#9881;&#65039; Setting gpuId to empty string
23:18:18.712 › &#128256; Setting model to null
23:18:18.715 › &#128256; Setting model to realesrgan-x4plus

```

Still fail to start Upscayl

How to uninstall flatpak Upscayl ?  Thanks

I'm prepared to try snap version.

Regards

---

### Post by satimis on 2024-11-03
Hi Dennis N,

On Internet searching, I found following thread;

**[COLOR="#FF0000"]Upscayl does not run in Ubuntu 24.04 due to apparmor issue #902[/COLOR]**
[https://github.com/upscayl/upscayl/issues/902](https://github.com/upscayl/upscayl/issues/902)

Would it be the same in Ubuntu 22.04?

Regards

---

### Post by 1fallen on 2024-11-03
Well it works here:
```
PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo
/etc/os-release
```
```
flatpak run org.upscayl.Upscayl

Note that the directories 

'/var/lib/flatpak/exports/share'
'/home/me/.local/share/flatpak/exports/share'

are not in the search path set by the XDG_DATA_DIRS environment variable, so
applications installed by Flatpak may not appear on your desktop until the
session is restarted.

[3:1103/103134.090008:ERROR:bus.cc(407)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
[3:1103/103135.110602:ERROR:bus.cc(407)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
[3:1103/103135.110645:ERROR:bus.cc(407)] Failed to connect to the bus: Failed to connect to socket /run/dbus/system_bus_socket: No such file or directory
&#65533;&#65533; DIRNAME /app/upscayl/resources/app.asar/export/electron
APPIMAGE env is not defined, current application is not an AppImage
10:31:35.151 &#8250; &#65533;&#65533; UPSCAYL EXEC PATH:  /app/upscayl/resources/bin/upscayl-bin
10:31:35.153 &#8250; &#65533;&#65533; MODELS PATH:  /app/upscayl/resources/models
10:31:36.515 &#8250; &#9881;&#65039; Setting saveImageAs to png
10:31:36.516 &#8250; &#65533;&#65533; Setting model to realesrgan-x4plus
10:31:36.518 &#8250; &#9881;&#65039; Setting gpuId to empty string
10:31:36.519 &#8250; &#65533;&#65533; Setting model to null
10:31:36.519 &#8250; &#65533;&#65533; Setting model to realesrgan-x4plus


```
EDIT:
```
sudo aa-status|grep upscayl
[sudo] password for me: 
   /app/upscayl/upscayl (19478) flatpak
   /app/upscayl/upscayl (19492) flatpak
   /app/upscayl/upscayl (19506) flatpak
   /app/upscayl/upscayl (19530) flatpak
   /app/upscayl/upscayl (19534) flatpak
   /app/upscayl/upscayl (19541) flatpak

```

---

### Post by satimis on 2024-11-03
Hi Dennis N,

On Internet searching, I found following thread;

**[COLOR="#FF0000"]Upscayl does not run in Ubuntu 24.04 due to apparmor issue #902[/COLOR]**
[https://github.com/upscayl/upscayl/issues/902](https://github.com/upscayl/upscayl/issues/902)

Would it be the same on Ubuntu 22.04?

Regards

---

### Post by 1fallen on 2024-11-03
> **satimis said:**
> 
 

**[COLOR=#FF0000]Upscayl does not run in Ubuntu 24.04 due to apparmor issue #902[/COLOR]**
[https://github.com/upscayl/upscayl/issues/902](https://github.com/upscayl/upscayl/issues/902)



](*,) Please read Post #18 again.....I just showed it works in 24.04.
That Ticket is very old July we have had 2 apparmor updates since.

Apparmor is not your problem, it is something else on your end.

---

### Post by ajgreeny on 2024-11-03
This post may do no more than increase the confusion but as I have many old faded photos I thought it worth trying Upscayl but I tried it as the appimage version 2.9.8

It opened fine though I did run command ```
sudo sysctl -w kernel.apparmor_restrict_unprivileged_userns=0
```to overcome the apparmor problem of certain electron apps (except VS Code) not working in 24.04.
That command may be no longer needed but I tried it without that command two days ago and it would not open or run at all. However when I started the appimage today I was immediately offered an upgrade of the version from 2.9.8 to this one, 2.11.5
Upscayl starts fine and appears to run but any jpg files dragged to it and saved as .jpg simply end up as a useless black image, nothing like the original though saving as a .png works fine 

I have never used any flatpack applications but I may try that next, however I wonder if anyone else has managed to get the appimage to work and produce a useful .jpg output image.

---

### Post by Dennis N on 2024-11-03
> Still fail to start Upscayl

Your output appears to show the program has started. Your problem is that the GUI window does not appear.
Are you using Wayland? If so, try Xorg session at login screen. Then try again to run it.
If the Flatpak fails with Xorg, I found a .deb file for Upscayl here:
[https://github.com/upscayl/upscayl/releases](https://github.com/upscayl/upscayl/releases)
That might work better for you.

---

### Post by 1fallen on 2024-11-03
> **Dennis N said:**
>  I found a .deb file for Upscayl here:
[https://github.com/upscayl/upscayl/releases](https://github.com/upscayl/upscayl/releases)
That might work better for you.

+100 Nice Job works every bit as good as the Flatpak :popcorn:

@satimis if you wish to remove the flatpak version use:
```
flatpak remove org.upscayl.Upscayl  
```
###And:
```
sudo flatpak repair

```
it cleans it out:
```
Working on the system installation at /var/lib/flatpak
[12/12] Verifying flathub:runtime/org.freedesktop.Platform/x86_64/23.08&#8230;
Checking remotes...
Pruning objects
Erasing .removed

```

If you want to Dump Flatpaks all together run:
```
 sudo apt autoremove --purge flatpak
```

---

### Post by 1fallen on 2024-11-03
> **ajgreeny said:**
> however I wonder if anyone else has managed to get the appimage to work and produce a useful .jpg output image.
It needs work ajgreeny, it's not as functionable.
```
'/home/me/upscayl-2.11.5-linux.AppImage' --no-sandbox

```

I don't like suggesting "sysctl -w kernel.apparmor_restrict_unprivileged_userns=0" many don't know why.
But for you and i it's ok, we know better. :)

Good Info here: Source: [https://discourse.ubuntu.com/t/spec-unprivileged-user-namespace-restrictions-via-apparmor-in-ubuntu-23-10/37626](https://discourse.ubuntu.com/t/spec-unprivileged-user-namespace-restrictions-via-apparmor-in-ubuntu-23-10/37626)

---

### Post by ajgreeny on 2024-11-03
I tried again using your suggested **--no-sandbox** option and this time no longer using that **sysctl -w kernel.apparmor_restrict_unprivileged_userns=0** as I had rebooted.

The appimage opened fine but unfortunately it could not save an image other than the full black one mentioned previously.
For now I've given up as it is not important enough for me to keep working on it though I may try the flatpack or the .deb version mentioned in post from **Dennis N** in post #22

**EDIT: One hour later.**
Just downloaded the .deb version and tried it but I still cannot get it to output anything other than a totally black image whether .png or .jpg so now I definitely have given up on it.

---

### Post by satimis on 2024-11-04
Hi all,

Upscayl problem solved finally as follow;

1. Uninstall Upscayl flatpak package
$ flatpak uninstall org.upscayl.Upscayl

2. Install Upscayl snap package
$ sudo snap install upscayl

3. Add Upscayl icon on the Menu bar

4. Click Upscayl icon to start the application
Upscayl started.

Please refer to the screenshot attached.

Regard

---

### Post by satimis on 2024-11-10
> **Dennis N said:**
> I tried your original image in Upscayl and I think I can get a much better result. Using Fast Real-Esrgan. You should try it out.

For corrections to contrast, gamma, saturation, color balancing etc. I use gthumb. Easy.
Hi Dennis N,

Just tried your advice.

"Fast Real-Esrgan" is on Step-2

Where is "gthumb" ? (pls refers to attached screenshot)

Thanks

Regards

---

### Post by satimis on 2024-11-11
Hi Dennis N,

Further to my last posting:

After Googling a while on Internet, it comes to my understanding Upscayl only increasing the resolution of an image but doing nothing on color and other problems.

However still I can't run it to upgrade image resolution.

&#128680; Error: Invalid GPU Device

Please refers to attached screenshot

Regards

---

### Post by Dennis N on 2024-11-11
If you Google with the error message "vkenumeratephysicaldevices failed -3 Error: Invalid GPU Device" you will get some results with suggestions. Hopefully one will work for you. My computer has Intel integrated graphics and I have no problems.

Unrelated to the error: Your scale is set to 8x which will produce a very big image file. Realize that the dimensions of the image will multiply by 8. So 500 x400 original will result in 4000 x 3200 pixels upscaled image and a very big file size as well. Too large for normal use.

---

### Post by satimis on 2024-11-11
> **Dennis N said:**
> If you Google with the error message "vkenumeratephysicaldevices failed -3 Error: Invalid GPU Device" you will get some results with suggestions. Hopefully one will work for you. My computer has Intel integr
Unrelated to the error: Your scale is set to 8x which will produce a very big image file. Realize that the dimensions of the image will multiply by 8. So 500 x400 original will result in 4000 x 3200 pixels upscaled image and a very big file size as well. Too large for normal use.ated graphics and I have no problems.

- snip - 
Hi Dennis N,

Before posting #28 I have googling a while.  Unfortunately I could not find a solution.  I'm running AMD Ryzen5 on my PC.

I have tried following commands on Terminal;
$ convert -enhance -equalize -contrast original.jpg improved.jpg

and 

$ convert -auto-gamma -auto-level -normalize original.jpg improved.jpg

They both work but the color quality is still poor.  I think I have to run GIMP or Darkroom to do the job.

I have no problem adding blue sky to old photos either online or on DaVinci Resolve.  It is very easy using online website, completely FREE

Regards

---

### Post by Dennis N on 2024-11-11
How about posting about your problem on the github discussion for Upscayl? You might get some results there.
[https://github.com/orgs/upscayl/discussions](https://github.com/orgs/upscayl/discussions)

---

### Post by satimis on 2024-11-14
> **Dennis N said:**
> How about posting about your problem on the github discussion for Upscayl? You might get some results there.
[https://github.com/orgs/upscayl/discussions](https://github.com/orgs/upscayl/discussions)
Thanks

---

### Post by Dennis N on 2024-11-15
If you're still interested in having a program on your computer, there is another upscaling program called Upscaler. It might work with your system. I had it installed a long time ago but replaced it with Upscayl because at that time, Upscayl had more options. However, looking at the Upscaler website. they seemed to have added features. Its Flatpak. Might be worth trying out.

Website:
[https://flathub.org/apps/io.gitlab.theevilskeleton.Upscaler](https://flathub.org/apps/io.gitlab.theevilskeleton.Upscaler)

Information from Flathub:

```
Upscaler - Upscale and enhance images

        ID: io.gitlab.theevilskeleton.Upscaler
       Ref: app/io.gitlab.theevilskeleton.Upscaler/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 1.4.0
   License: GPL-3.0
Collection: org.flathub.Stable
  Download: 49.4*MB
 Installed: 67.2*MB
   Runtime: org.gnome.Platform/x86_64/47
       Sdk: org.gnome.Sdk/x86_64/47

```

---

### Post by Dennis N on 2024-11-15
If you're still interested in having an upscaling program on your computer, there is another program called Upscaler. It might work with your system. I had it installed a long time ago but replaced it with Upscayl because at that time, Upscayl had more options. However, looking at the Upscaler website. they seemed to have added features. Its Flatpak. Might be worth trying out.

Website:
[https://flathub.org/apps/io.gitlab.theevilskeleton.Upscaler](https://flathub.org/apps/io.gitlab.theevilskeleton.Upscaler)

Information from Flathub:

```
Upscaler - Upscale and enhance images

        ID: io.gitlab.theevilskeleton.Upscaler
       Ref: app/io.gitlab.theevilskeleton.Upscaler/x86_64/stable
      Arch: x86_64
    Branch: stable
   Version: 1.4.0
   License: GPL-3.0
Collection: org.flathub.Stable
  Download: 49.4*MB
 Installed: 67.2*MB
   Runtime: org.gnome.Platform/x86_64/47
       Sdk: org.gnome.Sdk/x86_64/47

```

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> If you're still interested in having an upscaling program on your computer, there is another program called Upscaler. It might work with your system. I had it installed a long time ago but replaced it with Upscayl because at that time, Upscayl had more options. However, looking at the Upscaler website. they seemed to have added features. Its Flatpak. Might be worth trying out.
........
- snip - 
Hi Dennis N,

Thanks for your advice.

I'm now injecting my effort to restore fade old photos to digitised images at camera capturing stage.  Wonderful, there are many features(settings) on Android phone camera.  I just applied "filter" feature and it did a good job.  Please refers to attached screenshots.

I use remote-access controlling the Android phone camera.  Its setup, both hardware and software are very simple.  Also please refers to attached screenshots.

To convert. hard-copy photos of good quality to digitized images, we can use "google scan" on Android phone .  We just hold the phone camera with hands to shoot.  No hardware setup is required.  "google scan" is available on "Play store", FREE to use.

Besides we can shoot 4 (four) hardcopy photos in ONE shot simutaneously !!!

This is a NEW era !!!  We don't need a scanner.  Taking a shot is much much ... faster than scanning on a flatbed scanner !!!

Regards

---

### Post by Dennis N on 2024-11-15
Is this Google's PhotoScan app? If yes, I see the improvement between #1 and #2. I that works to your satisfaction, stop reading.

O.K, I just looked at the PhotoScan web page, and I didn't see any claim that it does upscaling (larger dimensions). If you want a larger size picture and improved sharpness, you need an upscaling application like Upscayl.  

What Upscayl (or Upscaler) does:
Your photo #1: 337.5 kB and 643 x 374
After processing with Upscayl using the 2x option: 1.6 mB and 1286 x 748.

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> Is this Google's PhotoScan app? If yes, I see the improvement between #1 and #2. I that works to your satisfaction, stop reading.
No.  That is from my Samsung Galaxy S22 phone with only one click after having selected the "filter".  It is very convenient.  I'm now googling the use of other settings.

> 
O.K, I just looked at the PhotoScan web page, and I didn't see any claim that it does upscaling (larger dimensions). If you want a larger size picture and improved sharpness, you need an upscaling application like Upscayl.  

What Upscayl (or Upscaler) does:
Your photo #1: 337.5 kB and 643 x 374
After processing with Upscayl using the 2x option: 1.6 mB and 1286 x 748.
I don't need big size digital images.  I just need those digitized images in good quality for building the website "My Foot Prints on the Earch".

If I need big size digitised images, after editing just run "Convert" command on Terminal to do the job.  Also it is very simple and convenient>

Regards

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> Is this Google's PhotoScan app? If yes, I see the improvement between #1 and #2. I that works to your satisfaction, stop reading.
No.  That is from my Samsung Galaxy S22 phone with only one click after having selected the "filter".  It is very convenient.  I'm now googling the use of other settings.

> 
O.K, I just looked at the PhotoScan web page, and I didn't see any claim that it does upscaling (larger dimensions). If you want a larger size picture and improved sharpness, you need an upscaling application like Upscayl.  

What Upscayl (or Upscaler) does:
Your photo #1: 337.5 kB and 643 x 374
After processing with Upscayl using the 2x option: 1.6 mB and 1286 x 748.
I don't need big size digital images.  I just need those digitized images in good quality for building the website "My Foot Prints on the Earch".

If I need big size digitised images, after editing just run "Convert" command on Terminal to do the job.  Also it is very simple and convenient.

Regards

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> Is this Google's PhotoScan app? If yes, I see the improvement between #1 and #2. I that works to your satisfaction, stop reading.
No.  That is from my Samsung Galaxy S22 phone with only one click after having selected the "filter".  It is very convenient.  I'm now googling the use of other settings.

> 
O.K, I just looked at the PhotoScan web page, and I didn't see any claim that it does upscaling (larger dimensions). If you want a larger size picture and improved sharpness, you need an upscaling application like Upscayl.  

What Upscayl (or Upscaler) does:
Your photo #1: 337.5 kB and 643 x 374
After processing with Upscayl using the 2x option: 1.6 mB and 1286 x 748.
I don't need big size digital images.  I just need those digitized images in good quality for building the website "My Foot Prints on the Earch".

If I need big size digitised images, after editing just run "Convert" command on Terminal to do the job.  Also it is very simple and convenient.

Just found this video
You're only using 10%... (Top 30 Unknown Galaxy S22 Ultra Camera Features!)
[https://www.youtube.com/watch?v=fgvRUBd17Hc](https://www.youtube.com/watch?v=fgvRUBd17Hc)

It is very useful to me

Regards

---

### Post by Dennis N on 2024-11-15
> If I need big size digitised images, after editing just run "Convert" command on Terminal to do the job
Convert command: You lost me there. What application is that?

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> Convert command: You lost me there. What application is that?
Imagemagick command

On Terminal:-
$ convert -resize 150% origin_image.jpg new_image.jpg
increasing the image size 50%

$ file new_image.jpg
will display its resolution/size

OR
$ identify new_image.png

Aslo I have Samsung Galaxy S24 Ultra mobile phone, even  with more advanced features in camera.  But I won't use it scanning my old photos.  I'll use my Samsung Galaxy S22 Ultra mobile phone because once mounted and setup, I won't remove it until finishing scanning 2,000 old photos.

Regards

---

### Post by Dennis N on 2024-11-15
OK, I'm installing Imagemagick to compare the result of using it with your command and what I get with Upscayl.

---

### Post by Dennis N on 2024-11-15
Test completed.
left: original image
center: resize x2 with Imagemagick and your command
right: using Upscayl x2

See the difference between center and right images. Upscayl (using Fast Real-Esrgan model) gives the sharpest result.

---

### Post by satimis on 2024-11-15
> **Dennis N said:**
> Test completed.
left: original image
center: resize x2 with Imagemagick and your command
right: using Upscayl x2

See the difference between center and right images. Upscayl (using Fast Real-Esrgan model) gives the sharpest result.
Please post the screenshot of your result on sharpening my old photo here  (sharpened on Upscayl).
 
I'm interested trying something new to me.  My problem here is unable making Upscayl to work.

I can make my old photo more sharper on Samsung Galaxy S22 Ultra phone camera, by playing round with its settings.  I only spent less than one minute to get my job done.

You're only using 10%... (Top 30 Unknown Galaxy S22 Ultra Camera Features!)
[https://www.youtube.com/watch?v=fgvRUBd17Hc](https://www.youtube.com/watch?v=fgvRUBd17Hc)

This video provides me more info on advanced settings of S22 phone camera.  My keen interest is to correct all problems of the old fade photos on upstream, i.e. on S22 phone camera, not to further editing the digitized images on computer with photo editing software.

PhotoScan &#8211; scanner by Google
It is a very interesting app on mobile phone, very easy and simple to use.

[B][COLOR="#FF0000"]Edit-1
====[/COLOR][/B]
If the size of the sharpened photo (my old photo) exceeding 350kB unable to upload, reduce its size with "convert" command running on Terminal```

$ convert -resize xx% original_image.jpg reduced_image.jpg

```

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]
Galaxy S22 ULTRA - The 10 Most UNIQUE & INTERESTING Features!
[https://www.youtube.com/watch?v=kq3AjBRR8KQ](https://www.youtube.com/watch?v=kq3AjBRR8KQ)

Instead of controlling its camera on PC running "remote access", its pen can control the camera without touching the phone.
(I just found this video.  I think I'll discover more on the functions provided by S22)

---

### Post by ajgreeny on 2024-11-16
For colour alone I have found **aaphoto** quite good and much more real looking than the examples shown on post #3.
It is not doing anything about the sharpness but I've never felt anything to be really worthwhile for correcting that if starting with a really fuzzy image.
Here's my original and corrected images attached.

---

### Post by Dennis N on 2024-11-16
> Please post the screenshot of your result on sharpening my old photo here (sharpened on Upscayl).
For the church, the Upscayl image is 1.7 mB, dimensions 992 x 1440.
If I upload that, the forum software is automatically resizing it to 67 kB, dimensions 529 x 768 so you can't obtain the real upscaled image by my posting it here.

---

### Post by satimis on 2024-11-16
Hi all,

Lot of thank for your advice.

Actually I was heading to a wrong direction.  I should look for how to enhance or upscale photos on Samsung Galaxy S22 Ultra mobile phone.  Shooting a hard-copy photo is only a step to import the photo to be edited to the phone.  Samsung has app to enhance/upscale photos - Galaxy Enhance-X.  It is available on Galaxy Store online, FREE.  Photos will be enhanced on the mobile phone.  Post editing after downing to PC is not necessary.

I'm now busy to get my Samsung Galaxy S22 Ultra mobile phone connected to Internet.  It doesn't has a SIM-card.   I got it connected via WiFi.  There are many applications on the phone to be updated because it has not be connected to Internet for long time, resting in desk drawer.

I'll come back after fixing other problems on my PC and the mobile phone, not relating to enhance photos.   

Thanks

Regards

---

### Post by Dennis N on 2024-11-16
> Galaxy Enhance-X. It is available on Galaxy Store online
The word 'enhance' could be applied to many types of image processing. Whether it involves AI technology like Upscayl is an open question. One would need to check the details of that particular app to know. It's possible it does, since the AI models are probably open source, and the phone is essentially a computer itself!

Be sure you are opening the images in post #43 in an image viewer to see the difference in quality between the center and right images. Especially note her hair.

Also, I suggest again you try the Upscaler program mentioned in post #34 to see if it works on your machine. It also uses AI.

---

### Post by satimis on 2024-11-16
> **Dennis N said:**
>  - snip -
Also, I suggest again you try the Upscaler program mentioned in post #34 to see if it works on your machine. It also uses AI.
Sorry, I don't follow.  It is still Upscaler?  Pls refer to screenshot

Regards

---

### Post by Dennis N on 2024-11-16
> **satimis said:**
> Sorry, I don't follow.  It is still Upscaler?  Pls refer to screenshot

Regards

**Upscayl** and **Upscaler** are two different applications that do the same task. Since Upscayl did not run for you, I thought you might want to install and try the other one (in your image) and see if it will run ok. I hope it does!

---

### Post by satimis on 2024-11-18
Hi all,

I have tested Galaxy Enhance-X on my Samsung Galaxy S22 Ultra mobile phone.  The latter is connected to Ubuntu 24.04 desktop PC via an USB cable.

Remote Access (Remote desktop access) is set up and working perfectly.  I did all operation on desktop PC.  This is wonderful setup.  Files can be drag-&-drop between S22 screen and Ubuntu 24.04 screen on the PC display.

The quality of the digitized image is improved on Galaxy Enchance-X app.  Please refer the attachments uploaded.  It only took 2~3 minutes to finish one job, adjusting the settings and selecting tools.  I can make the quality of the digitized image better.  It is directly proportional to my time injected.

Now I'm heading to solve following 2 points:-
1) Add a blue sky on the digitize image (I have done it now but the quality not good enough)
2) Rotate the screen of S22 phone on PC display 90 degree (hozontally).  I can adjust the screen of S22 phone but now it is on vertical position, not much space for me to increase its size.
For graphic editing I need doing it on a large screen

Remark:
The photos uploaded are reduced to 40% of their original size

Regards

---

### Post by satimis on 2024-11-20
Hi all,

_[COLOR="#FF0000"]Add Blue Sky to photo on Samsung Galaxy S22 Ultra phone - I got it done !!![/COLOR]_

Why the sky on the photo attached on my post#51 above is not blue to eyes, because the sky is too small.

I added "blue sky" to the photo "ferrara-02.jpg" attached on my posting #1.   I got a blue sky on it.  Please refer to the file attached.

My remaining problem is;
2) Rotate the screen of S22 phone on PC display 90 degree (hozontally)

Regards

---

### Post by satimis on 2024-11-20
Hi all,

Further to my post #52 above, it is possble adding an even more beautiful sky to photos on Galaxy S22 Ultra phone.  Please refers to attached screenshot

There are many other advanced features for photo editing on Galaxy S22 Ultra phone.  PICNIC is only one photo editing App running on Galaxy S22 phone.  There are many other photo editors running on the said phone as well.

An Android phone has multiple functions:
1. A mini computer for running App
2. A scanner with super fast scanning speed - just taking a shot
3. A camera for taking photos and video
4. A photo editing device with multiple advanced features
5. A phone for voice communication
6. A Recorder and Player of Sound File
etc.

A flatbed scanner can only scan photos and documents at slow speed.

---

### Post by satimis on 2024-11-21
Hi all,

Samsung Galaxy S22 Ultra phone has done another excellent job, restoring old fade photo of >25 years.

Steps performed:
1.  Captured the old photo on S22 phone camera, with camera settings
2.  The digital image was further edited on the phone with Galaxy Enhance-X and PICNIC.
3.  Time spent about 10 mins

Remark: all operations are performed on Ubuntu 24.04 desktop PC

Please see attached photos.  
Upload photos = 20% their original sizes

Regards

---

