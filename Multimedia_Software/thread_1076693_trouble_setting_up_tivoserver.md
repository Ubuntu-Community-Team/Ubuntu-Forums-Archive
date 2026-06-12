---
title: "trouble setting up tivoserver"
date: 2009-02-21
forum: Multimedia Software
---

### Post by newseamus on 2009-02-21
unbuntu 8.10

I am trying to install tivoserver program from sourceforge.
I follow directions from engadget walkthhru here:
[http://www.engadget.com/2006/09/12/how-to-serve-video-to-your-tivo/](http://www.engadget.com/2006/09/12/how-to-serve-video-to-your-tivo/)
but their instructions do not work for me.

I can get the .tgz version to open into a folder but none of the executables in that folder will start.

If I download the .gz version as recommended by engadget I get a lone executable that will not open.

anybody have success installing tivoserver another way?

thanks
( I am brand new to ubuntu so I am unsure if I am providing enough detail for my problem)

---

### Post by mattisking on 2009-03-24
I realize this is a bit late... but I can help, I believe. You want to download the Linux Version as Engadget suggests: 
[http://downloads.sourceforge.net/tivoserver/tivoserver-0.4.3-linux.gz?use_mirror=voxel]("http://downloads.sourceforge.net/tivoserver/tivoserver-0.4.3-linux.gz?use_mirror=voxel")

Let the Archive Manager open it for you by default and you'll see there's a single file inside. If I sound at all like I'm talking down to you, please don't take it that way. A couple of the things you said seem to indicate you are very new to Linux (although you mention being new to Ubuntu that doesn't mean you're new to Linux).

You'll see a single file inside. The file will have no extension, per-se. Extract the file to your home directory. You could setup your own personal bin directory if you like under your home directory and save it there or just put it in home. This will likely be the default place that opens up when you hit the Extract button.

Once the file is saved, you'll want to Execute it. Keep in mind that this isn't quite the same as it is in Windows. In Linux, any file can theoretically be "executable" by simply adding the rights to the file. Engadget did explain that to some extent though if you're new, it might not have made sense.

You'll want to run the Terminal window. You can run that by going to your Gnome Menu, choosing Accessories, and then Terminal. You will be greeted by what looks like a command prompt on Windows... Your default directory will be your home directory. type "ls" (without the quotes) and hit enter and you'll see a directory listing, which should also include the file you extracted, tivoserver-0.4.3-linux.

We need to "make it executable" so type this and hit enter:
chmod 755 tivoserver-0.4.3-linux

Next, let's go ahead and execute it. You don't do this by double-clicking it like you may be used to in Windows. Sometimes in Linux it's necessary to give bash (your terminal) information on where the file is you want to execute, even when it's in the directory you're in so when we execute it, we're going to tell it, run this file in this directory... type this and hit enter:
./tivoserver-0.4.3-linux

You should see it write several things to your terminal window... it might complain that it could not find your video directory. Ubuntu, at least as of Intrepid and Jaunty (not sure how far it goes back) creates a folder called Videos in your home directory but this application is looking for a folder called "video".

We could rename the folder, but let's just reconfigure tivoserver instead. In Linux, some applications write their configuration information to a global configuration store, similar in thinking at least to the Windows Registry. Most, however, write to a somewhat hidden location within your Home directory. In most terminal settings, you won't by default, see files or folders that start with a (dot). If tivoserver stopped running and you're sitting at your prompt again in the terminal, type ls as before but add -al and hit enter like this:
ls -al
That says, give me a directory listing, but show ALL files (a) and in long format (l). On the far right of each line is the file or folder name. You should see alot of files and folders that start with a (dot). Most linux applications will store their configuration files there.

In your terminal:
cd .tivoserver
ls

You should see:
cache
settings.cfg
settings.cfg.new

Let's edit settings.cfg using a nice easy graphical editor much like Notepad in Windows... from your terminal:
gedit settings.cfg

Scroll down until you find the line beginning with:
VIDEO_DIR=/home/....

Change the end of that line from "video" to "Videos".
Save and exit gedit.
Terminal:
cd ..
./tivoserver-0.4.3-linux

When you put video files inside that Videos folder now, they should show up as Engadget described. 

You can minimize that terminal window... but you can't close it or you'll close tivoserver. There may be instructions somewhere on how to setup tivoserver as a proper daemon (like a Windows Service) that can run on it's own in the background whether you are logged in or not, but it's not necessarily simple to do that in Linux and permissions can be a major issue. See if that works for you.

---

### Post by tindallh on 2009-04-03
I had similar issues...  I'm running a MythBuntu box, and wanted to share out all the files using tivoserver so the kids could see the shows (we only have on Digital TV receiver, the Mythbuntu box).  The catch:  I'm running a 64-bit version of Ubuntu on that box.....  And so I got:
```
root@mythtv:/usr/local/bin# ./tivoserver-0.4.3-linux
./tivoserver-0.4.3-linux: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
if you do a "ldd tivoserver-0.4.3-linux", you should see something like this:
```

root@mythtv:/usr/local/bin# ldd tivoserver-0.4.3-linux
        linux-gate.so.1 =>  (0xf7f1d000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7f08000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf7eef000)
        libstdc++.so.5 => not found
        libm.so.6 => /lib32/libm.so.6 (0xf7ec8000)
        libgcc_s.so.1 => not found
        libc.so.6 => /lib32/libc.so.6 (0xf7d6a000)
        /lib/ld-linux.so.2 (0xf7f1e000)

```
The problem is, the files ldd is saying are "not found" are really there, they're just the 64-bit versions!  I found and installed the 32-bit versions of some of the libraries using synaptic to install "lib32stdc++6-4.3-dbg", which solved all but the libstdc++.so.5.  I happen to have another Ubuntu box, running 32-bit, so I simply copied that file to the /usr/lib32 directory on my 64-bit box....  Maybe not the ideal way to do it, but it worked. 
One other note, I still get the dreaded "no such file or directory" message when trying to start the program in the standard terminal window on my Mythbuntu box, but it starts fine when I SSH in from another box...  I installed Eterm on the mythbuntu box and it'll start fine using that.  Maybe a reboot would fix the problem in the normal shell, but I was busy recording and too impatient to wait..... 
Hope some of this helps somebody!

---

