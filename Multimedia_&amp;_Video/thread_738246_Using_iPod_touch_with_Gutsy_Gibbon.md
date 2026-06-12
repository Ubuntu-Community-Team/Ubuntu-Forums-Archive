---
title: "Using iPod touch with Gutsy Gibbon"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by VIPea on 2008-03-28
[COLOR="Red"][SIZE="3"]Hi! I've tried to follow the instructions on how to do this here[/SIZE][/COLOR]-  [https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone")

> A third party source provides the **ipod convenience** package needed to properly mount and unmount an iPhone or iPod Touch, and for gtkpod users, a newer gtkpod is required for the iPhone and iPod Touch.

  **1.**      Click **System &#8594; Administration &#8594; Synaptic Package Manager** (You can skip this step on Ubuntu 8.04 as the relevant packages have been added in the Universe repository)

Once Synaptic starts, click **Settings &#8594; Repositories &#8594; Third Party Software**. Click Add and use **deb** [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) **gutsy main** as the APT line. (this source should have a key file to avoid the prompt to install without authentication).

   **1.**      Click **Reload**   
   **2.**     Before installing newer packages, make sure to first uninstall **libgpod**.   
   **3.**     Install the **ipod-convenience** package, as well as either **amarok** or **gtkpod** (or both if you like). When asked, enter the IP address of your iPod Touch or iPhone that you selected earlier. When asked for a folder to mount your iPod Touch or iPhone, either leave the default of **/media/ipod** or another folder if you prefer - just remember to use that folder name for rest of this guide. The package will make the folder for you.

[SIZE="2"][COLOR="Blue"]I can't manage to find or install **ipod-convenience**, I've already got **amarok** and I've tried adding the repository.[/COLOR][/SIZE]

[SIZE="2"]Please help me so that I'll be able to sync my iPod with amarok.[/SIZE]


**P.S.** Yes, my iPod is jail-broken and I have BSD Subsystem as well as Open SSH

---

### Post by Kaare_K on 2008-03-29
Hey there, I'm pretty new but just added my ipod touch to my system. I had the same problem, but to find the ipod convience package you have to... 

GO to system, Administration, and then down to synaptic package manager and then just scroll all the way down to it! I couldn't find it in the add/remove program so I just checked there. Hope that helps!

Kaare.

---

### Post by ntetreau on 2008-03-29
Once you have added the PPA repositories, you need to do an "update" or "reload" (sorry, I' m not at home at the moment), so that the list of packages is renewed.  You should then be able to  "Find" ipod-convenience, libgpod3 (make sure to remove libgpod2 first), amarok and gtkpod.  Then keep following the wiki to the letter and it should work.

---

### Post by VIPea on 2008-03-29
Thank you both! 

I'll try it as soon as my update manager is done :)

---

### Post by VIPea on 2008-03-29
Ok, I've managed to install **ipod convenience** but when I try to mount my device I get this error - ```
 ipod-touch-mount
touch: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.
```

and if I try the command with sudo this is what I get - 
```
 sudo ipod-touch-mount
Please add yourself to the fuse group, logout/in and try again.
```

---

### Post by ouilsen on 2008-03-29
System -> Users and Groups

Click on your user then "manage groups"

select fuse -> properties -> select your user.

Now log out. Only restarting the terminal won't work. I really had to log out from my session or ALT + F1 to the console.

Now ipod-touch-mount should work.

Hope this helps.

Edit: Oh and in case you played with the permissions of /media/ipod: They should be user=root and group=fuse with 755.

---

### Post by VIPea on 2008-03-29
Thank you very much, this appears to have worked. I connected to my iPod in Amarok..
[B]BUT! When I tried transferring a song it didn't appear on my iPod. So I turned it off and back on. 
Now when I try access my music or videos it says[/B] "*No Content*".

Tried deleting the song off my iPod and restarting. Still says "*No Content*".
**Please help**

---

### Post by VIPea on 2008-03-30
Please help!

---

### Post by ntetreau on 2008-04-10
Hey, are you sure you have configured Amarok to use the xiPhone as type of ipod?  Also, check the wiki and redo all the steps, making sure you have the firewireid for example.  On which firmware are you?  I've seen people having problems with firmware <1.1.3 as iphone-mount checks if the directory /var/mobile exist.  If it does (other apps could create it), it assumes that you have a firmware >= 1.1.3 and put your music in the wrong folder.  Now that i think of it, make sure you only have libgpod3 installed not libgpod2!

---

### Post by ntetreau on 2008-04-10
You should post your problem in the main iphone and ubuntu thread.  Most people able to help get notification when new posts are added to this thread:  [http://ubuntuforums.org/showthread.php?p=4682507](http://ubuntuforums.org/showthread.php?p=4682507)

---

### Post by adz666 on 2008-05-03
i have the same problem but i cant get past the mount bit. ive added the fuse thingy (sorry but im not very technical minded) but it now says

> sudo ipod-touch-mount
ping: unknown host ipod
iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this.

---

