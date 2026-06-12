---
title: "Samsung Galaxy Nexus Mounting Problems 12.04 64bit"
date: 2012-05-07
forum: Multimedia Software
---

### Post by tgwaste on 2012-05-07
Hello,
 I am running 12.04 64bit and no matter what I do or what method I try things lock up when I try to mount my Galaxy Nexus filesystem.

When issuing a mount any attemp at say 'ls' of a directory the mount is in will freeze the 'ls'.

ie:  ls /media/GalaxyNexus

just freezes.

Its not until I UNPLUG the phone that it unfreezes and thinks its mounted.

11.10 worked fine.  Any ideas?

---

### Post by xyverz on 2012-09-01
Yes. This is a problem with the 64-bit mtpfs package having a bug. The version of the package available in the repos has this bug.

I downloaded the source code from the maintainer's website, compiled and installed it. After that, I'm able to access my filesystem again. I did need to install the following in order for ./configure to work:

libfuse-dev
libmtp-dev
libmad0-dev
libid3tag0-dev
libid3-tools (I don't believe this was a requirement, but I made sure it was installed anyway)

Of course, I already had build-essential installed. If you don't have that installed, you'll need to apt-get install that as well.

Once those dependencies were installed, I did a make && sudo make install, and re-plugged my Nexus back into my box. *bamf!* everything worked again. =)

Hope this helps!

--X...

---

### Post by maloo on 2012-10-10
I haven't had much luck with mtpfs at all. I followed your hint xyverz and compiled and installed mtpfs from [http://www.adebenham.com/files/mtp/mtpfs-1.1.tar.gz]("http://www.adebenham.com/files/mtp/mtpfs-1.1.tar.gz") however I still couldn't cd or ls any files on my galaxy nexus.

So I had a look around and found [go-mtpfs]("https://github.com/hanwen/go-mtpfs") 
I downloaded the latest 64bit precompiled binary from [http://hanwen.home.xs4all.nl/public/software/go-mtpfs/]("http://hanwen.home.xs4all.nl/public/software/go-mtpfs/") and it has been working great.
To install on my box I did the following in a terminal:
```
wget http://hanwen.home.xs4all.nl/public/software/go-mtpfs/go-mtpfs.eb0de182.x86_64
sudo mv go-mtpfs.eb0de182.x86_64 /usr/bin/go-mtpfs
sudo chown root.root /usr/bin/go-mtpfs
sudo chmod 755 /usr/bin/go-mtpfs
sudo mkdir -p /media/nexus
sudo chmod 777 /media/nexus
echo "alias mount-nexus='go-mtpfs /media/nexus &'">> ~/.bashrc
echo "alias umount-nexus='fusermount -u /media/nexus'">> ~/.bashrc
```

Then once that is done to mount your nexus just type in a terminal:
```
mount-nexus
```
and to umount type:
```
umount-nexus
```
You will then be able to see all of your files under /media/nexus

I also had some issues with the nexus automounting however I disabled this by intalling dconf-tools and following this: 
[https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

BTW I'm running Linux Mint 13 Cinnamon Edition x64.

Hope that helps!

---

### Post by cortman on 2012-10-10
I'm having trouble with maloo's method above- all goes great but it won't mount, and gives me the following error in the terminal (a minute or so after running "mount-phone")-

```
cortman@gwaihir:~$ PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
2012/10/10 12:25:01 rdev.open: open: open returned nil

```

Anyone have any ideas?

---

