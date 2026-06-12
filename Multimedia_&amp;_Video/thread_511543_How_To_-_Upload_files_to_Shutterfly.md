---
title: "How To - Upload files to Shutterfly"
date: 2007-07-27
forum: Multimedia &amp; Video
---

### Post by DugieHowsa on 2007-07-27
There are many on-line photo sharing web sites out there.  Flickr probably has the most utilities and functionality due to its available API, but has limited free storage.  I like to use Shutterfly, as it has:

1)  Unlimited free storage
2)  Custom URL for your collections (such as yourname.shutterfly.com)
3)  A nice user interface for admins and guests (in my opinion).

BUT, it does not have an API for developers, and does not have any utilities and browser plugin-ins for linux... kind of.

There is a Shutterfly SmartUpload utility for linux, but it is no longer being developed or supported by Shutterfly.  You can no longer download the utility from the Shutterfly web site, but there is a way to download and install this utility.

1)  Download the Shutterfly SmartUpload utility from Softpedia.

   [http://web1.shutterfly.com/downloads/sflysusw-1.1.0-6.tar.gz](http://web1.shutterfly.com/downloads/sflysusw-1.1.0-6.tar.gz)

2)  Extract the file.

    tar -xvf sflysusw-1.1.0-6.tar.gz

The README.txt lists all the packages that the sflysusw program is dependant on.  A few of them are not installed by default in Ubuntu, so you will have to install them manually before the program will run.

NOTE:  These are the packages I had to install.  Your experience may differ, but the concept is the same.

3)  Install dependencies:

   sudo apt-get install libttf-dev

   sudo apt-get install libstdc++2.10-glibc2.2

 4)  The last dependency is not in the Ubuntu repositories, so you will have to download it manually:

   [http://www.imakmud.com/libstdc++-libc6.1-1.so.2](http://www.imakmud.com/libstdc++-libc6.1-1.so.2)
      (From this post:  [http://ubuntuforums.org/showthread.php?p=3068820](http://ubuntuforums.org/showthread.php?p=3068820))

   sudo cp libstdc++-libc6.1-1.so.2 /usr/lib/

5)  Copy the sflysusw executable to your desktop.  From here, you can rename it to what ever you want, and then double-click to run it.

If you wish to customize the application further, you can edit the .sfupl file in your  home directory.

---

### Post by bean77 on 2007-08-16
Hi-I followed the first steps but when I try to open the readme file there is nothing there...

---

### Post by cutiger95 on 2007-12-22
Alright everyone I am stuck on this install and my wife is about ready to kill me as it is on her laptop.

Her one request is that she be able to upload bulk photo's to shutterfly.  The IE interface allows this, but no other browsers have the functionality nor do the idgets at shutterfly make exceptions for this.

So I have been beating my head against the wall trying to hit the above list of things to do.  Everything appears to be OK except that when I double click on the shutterfly .exe that is on my desktop I get nada, nothing.

Any help would be appreciated, I am a newbie for sure.

---

### Post by helpdeskdan on 2007-12-25
This thing is junk - it won't upload at all.  Starts to upload and then stalls - won't do anything.  Too bad, it looked decent, and I was really happy to see linux supported. 

**Thanks a bunch for the howto, Dugie!**  Yeah, it doesn't work, but at least I was able to find out quickly instead of struggling to discover the steps.  You saved me a ton of time. 

Cutiger - you're trying to run an exe on linux.  Won't work without wine.  Wine can be difficult to use for newbies.  Google "wine ubuntu."

I did find that SmartUpload 2.2 runs in Wine.  (Shutterfly studio does not - don't bother trying)  However, the icons are somewhat garbled so it is much harder to use.  And, sometimes it seems to crash on startup.  (It has only done this once to me, but it was a hard crash) Keep a processor/load window open and, if you start to see it zoom, kill it QUICK!

[web1.shutterfly.com/downloads/ShutterflySmartUpload22.exe]("web1.shutterfly.com/downloads/ShutterflySmartUpload22.exe")

I'm not sure what the first window is when you launch it (registration? Definitely select "don't ask again"), just click on stuff till it goes to the next window. Then click no till you get to the Shutterfly smart upload utility. This works reasonably well for uploading despite the garbled icons. Select the photos you want while holding down the shift or control keys to select multiple images.  

It did crash my computer one time on launch (100% CPU), so I stress, **save ALL work before you run it**.  Once it starts uploading, don't touch it!  Don't click the show details button - sometimes it works, sometimes it crashes it.  The icons are messed up anyway, it won't show you much.  Don't so much as move a window over it - this setup is about as stable as a disgruntled postal worker.  Tweaking wine settings hasn't made much difference in stability.  (In fact, it actually seemed to be less stable with a virtual desktop)

Hopefully, this information I have posted will help somebody out.

Update: The program seems to almost always crash when it's done uploading.  You'll see your processor spike when it does.  Force Quit.  Be sure you know how to kill processes from the command line because sometimes it locks up on start and there is no way to kill it from X.  Things to try: pkill -9 sfupload.exe, pkill -9 explorer.exe, pkill -9 wineserver, pkill wine, ect.

---

### Post by dday376 on 2008-01-31
I have been struggling with getting ShutterflyStudio to work.  It's the last application I have to get working before I can comfortably move my wife over to Ubuntu.  Anyhow, I've been playing with wine for several days now, and while I haven't quite gotten it to work directly, I've made progress and this looked like a good thread to post to.

My goal is to get it installed stand-alone.  I'm using winetricks.sh ([http://kegel.com/wine/winetricks]("http://kegel.com/wine/winetricks")) to get various windows components, but as I said, no luck there.

But....  I took a shot using the ies4linux ([http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")).  Basically, I installed IE6 using ies4linux.  In a shell, I then set my WINEPREFIX to where ies4linux installed.  I used the default, so this was in ~/.ies4linux/ie6.  I then installed ShutterflyStudio.

```

export WINEPREFIX=~/.ies4linux/ie6
wine ShutterflyStudioInstaller.exe

```

It complains about being on Windows 98, but it works.   I have not tested it out completely, but hopefully posting here will help get some attention on going this route.  

I suspect Picasa is not so different than the ShutterflyStudio with respect to components used, so another option to try might be to install it into the same wine folder as Picasa:

```

export WINEPREFIX=~/.picasa
wine ShutterflyStudioInstaller.exe

```

In the meantime, I'll keep playing around!

**Updated 2008-02-02:**  The latest Beta release of Picasa for Linux will permit you to upload directly to shutterfly.  I'm still going to mess around with this, but I use Picasa and it is a nice alternative to Shutterfly Studio.

---

### Post by helpdeskdan on 2008-02-16
PIcasa, eh?  I'll try that - thanks.

---

### Post by nattynu on 2008-02-18
Picasa2 works well for bulk Shutterfly uploads. Select photos and take the 'Order Prints' option and provide your Shutterfly credentials.

---

### Post by helpdeskdan on 2008-02-22
Thanks - that seems easy enough - if it works, why even bother with Shutterfly's programs?

---

### Post by helpdeskdan on 2008-06-03
Picassa would be GREAT - if it didn't STALL every time I try to upload!!  I love that program.  I still use it to edit the pictures.

Last time, it stalled after just 4 pictures.  So, back to shutterfly under wine.  I created a text file with this:

pkill -9 sfupload.exe
pkill -9 explorer.exe
pkill -9 wineserver
pkill wine

called kill_shutterfly.  Then I did a chmod +x kill_shutterfly.  Finally, I added the system monitor to my top panel, and a link (hint - right click and select add to panel) to the tiny kill_shutterfly text tile.  If I ever see the processor suddenly go high (hasn't happened in a while - perhaps they fixed it), I just click the "Kill Shutterfly" button.  Not the best setup, but, it works!

---

