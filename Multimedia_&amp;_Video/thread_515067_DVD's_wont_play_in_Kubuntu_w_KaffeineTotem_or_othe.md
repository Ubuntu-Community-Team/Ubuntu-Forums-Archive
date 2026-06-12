---
title: "DVD's wont play in Kubuntu w/ Kaffeine/Totem or other player"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by Uber Nooblett on 2007-08-01
Hey, I'm fairly new to K/Ubuntu but I've been able to sort most of my issues (apart from not being able to save NVidia settings at the mo and unsure what to edit xorg.conf to so not gonna risk it just yet :P )
My issue at the moment is one for which I have not found a previous post that matches my issue:

When trying to play a DVD (this is the first time I have tried) I get an error message (in Kaffeine) saying either:
[I]
[B]"the source can't be read. 

Maybe you don't have enough rights for this, or this source doesn't contain data (e.g: no disc driver). (Encrypted or faulty DVD)"[/B][/I]

or
[I]
[B]"the source can't be read. 

Maybe you don't have enough rights for this, or this source doesn't contain data (e.g: no disc driver). (Error reading NAV packet)"[/B][/I]

depending on the drive I use.

This is the same with any DVD I insert.

Any ideas? Would be nice to have DVDs up and running :)

Thanks in advance

---

### Post by Andrew-buntu on 2007-08-01
Have you installed libdvdcss and all that good stuff yet?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Uber Nooblett on 2007-08-01
> **Andrew-buntu said:**
> Have you installed libdvdcss and all that good stuff yet?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I havent ventured there yet no, I didnt know this was necessary.

I'm a little unsure what I need from the details there, it took me into directory after directory and I really wasnt sure what I really need to download for my system :S there's so many diff ones

I'm running an AMD 64 x2 4000 with a Geforce 8800 GTS if that info helps any

thanks for your quick response :)

---

### Post by Uber Nooblett on 2007-08-01
I believe I have now installed libdvdcss2, but still no joy, same message in kaffeine

---

### Post by Andrew-buntu on 2007-08-01
Did you install the other packages mentioned, too?  libdvdcss will unencrypt DVDs but you need a few more packages to read the video and browse the menu.  Try typing this into a terminal:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```

---

### Post by Uber Nooblett on 2007-08-01
> **Andrew-buntu said:**
> Did you install the other packages mentioned, too?  libdvdcss will unencrypt DVDs but you need a few more packages to read the video and browse the menu.  Try typing this into a terminal:
```
sudo apt-get install libdvdread3 libxine1-ffmpeg
```

I just got this when I typed what you said:

[img]http://img412.imageshack.us/img412/1479/snapshot6um2.jpg[/img]

---

### Post by PFilter on 2007-08-01
That is a "one" not an 'L" on the end of xine1--mpeg.

---

### Post by Uber Nooblett on 2007-08-01
> **PFilter said:**
> That is a "one" not an 'L" on the end of xine1--mpeg.
[img]http://img169.imageshack.us/img169/9657/snapshot7ev1.jpg[/img]

---

### Post by phreeq on 2007-08-01
I'm having the same problems. I have libdvdcss2, libdvdnav4, libdvdplay0 and libdvdread3 installed. I used Automatix to add the dvd codecs, but still no luck.

---

### Post by RomeReactor on 2007-08-01
Hi **phreeq**. Are you using Totem to play the DVD? If so, try to change it to **totem-xine**--if you haven't made any changes other than install the libdvd* libraries, you're using **totem-gstreamer**, which can sometimes be problematic with DVDs. To install totem-xine, go to "System->Administration->Synaptic Package Manager" and search for it. If you're also on Kubuntu or using KDE in Ubuntu, search for it in Adept. Or, from the command line:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```
and then try the DVD again.

---

### Post by phreeq on 2007-08-02
RomeReactor,

I have tried to open the DVD with totem-gstreamer, totem-xine, vlc, mplayer, acidrip, dvd95, dvd::rip and dvdshrink. As far as the packages you recommended, I already had all of them installed.

Thanks for trying, I appreciate it!

---

### Post by RomeReactor on 2007-08-02
Some people have said that using **regionset** to set their DVD region solved the problem for them; maybe you could give it try, though I don't know if this is the case for you. If you want to install it You can find it in Synaptic, or:
```
sudo apt-get install regionset
```

---

### Post by phreeq on 2007-08-02
Hey, it was worth a try, but that didn't fix it...seeing as how I am not in a position where I need this to work on this computer, I am really not stressing over it.

Thanks again!

---

### Post by RomeReactor on 2007-08-02
Seeing as you used Automatix to install the codecs, maybe their [support forums for Feisty]("http://www.getautomatix.com/forum/index.php?showforum=45") would provide you with specific help; [here's a thread]("http://www.getautomatix.com/forum/index.php?showtopic=1234&hl=libdvdcss") from that forum that could be useful.

---

### Post by TKR101010 on 2007-08-02
> **RomeReactor said:**
> ```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs
```

Thanks for that info. This almost worked for me. At least Movie Player could read the copyright warnings at the beginning of the DVD, but couldn't progress past them. It says I need to have libdvdcss. So I tried ...

sudo apt-get install libdvdcss

... but got ...

Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate

so I guess I now have to find out where I can get this libdvdcss.

---

### Post by RomeReactor on 2007-08-02
Hi. Looks like you don't have the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") repositories, which is where you get **libdvdcss**; according to the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats#head-e69e0c62de07b1e2b560c1ad6b68823328906067") you need to add them and then install the package. From the terminal (Applications->Accessories->Terminal) enter the following:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
to add the repositories to your **/etc/apt/sources.list** file;
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
to get the gpg key (to authenticate them and update the package managers); and
```
sudo apt-get install libdvdcss2 libdvdnav4 libdvdplay0 libdvdread3 totem-xine libxine1-ffmpeg libxine-extracodecs
```
to install the necessary packages (it will probably tell you that most of them are already installed).

---

### Post by TKR101010 on 2007-08-02
Thanks for the info. I had found the libdvdcss at ...

[http://download.videolan.org/pub/libdvdcss/1.2.9/deb/](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/)

... installed it, and was able to read dvds fine afterward. I went ahead and did your method as well in case there was something that I might need for later. :)

---

### Post by RomeReactor on 2007-08-02
Just noticed that the first command I gave you was for Dapper; If you have Feisty, you'll have to remove the entry from /etc/apt/sources.list:
```
gksudo gedit /etc/apt/sources.list
```
look for an entry that mentions Medibuntu, which might read like this:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ dapper free non-free
```
Delete it and add this instead:
```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
```
Save the file and close the text editor, and update the repositories:
```
sudo apt-get update
```

Sorry for the mistake.

---

