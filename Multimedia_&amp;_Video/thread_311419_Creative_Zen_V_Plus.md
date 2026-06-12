---
title: "Creative Zen V Plus?"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by Guns90 on 2006-12-02
Good Evening,

I did a search but could not find a thread confirming whether the Creative Zen V Plus 2 Gb player will work with Linux (32 and 64 bit versions).  Does anyone have one, and if so, would you please let me know how it works?  Thanks


Gary

---

### Post by JayTee on 2006-12-03
I'm not 100% certain about the Zen but my Creative Muvo works fine. I just plug it in and it automounts. I can drag and drop my mp3 files onto the flash drive and I'm good to go. I just recently bought a 2GB SanDisk Rhapsody e250R and that also works like a champ. I looked at the Zen but ended up choosing the SanDisk because it was on sale and it also had a microSD slot to add more storage.

---

### Post by bapoumba on 2006-12-03
Hi,
I have a Zen micro, which runs fine with [gnomad2,]("http://gnomad2.sourceforge.net/") universe repositories.

---

### Post by Guns90 on 2006-12-03
I appreciate the responses, guys.  

I too have a Creative product, the Zen Nano Plus 1Gb; and it works fine with my 32 bit system; however, the Zen V Plus (which I'm assuming is the replacement for the Nano Plus) is a new generation, so there is no guarantee that it works like its predecessors.  I'm also concerned if there will be any conflicts because it will be used with a 64 bit system the boys are getting for Christmas.   

Gary

---

### Post by ButteBlues on 2006-12-03
The Zen V works under gnomad2 using the FAQ on this forum.

Also, if you've built the libmtp as per the above-mentioned instructions, and you install the Feisty build of Amarok 1.4.4, then it'll work with Amarok as well. :)

---

### Post by Rodneyck on 2006-12-03
> **a simple façade said:**
> The Zen V works under gnomad2 using the FAQ on this forum.

Also, if you've built the libmtp as per the above-mentioned instructions, and you install the Feisty build of Amarok 1.4.4, then it'll work with Amarok as well. :)

Do you know if the Creative Zen Micro will work with Amarok under Fiesty?

---

### Post by ButteBlues on 2006-12-03
Almost definitely. :)


Just do the following:

```
sudo apt-get install build-essential libnjb-dev libid3tag0-dev libglib2.0-dev libgtk2.0-dev libxml-perl checkinstall


mkdir libmtp


cd libmtp/
```

Download the following file to libtmp dir: [http://prdownloads.sourceforge.net/libmtp/libmtp-0.0.21.tar.gz?download](http://prdownloads.sourceforge.net/libmtp/libmtp-0.0.21.tar.gz?download)

```
tar -zxvf libmtp-0.0.21.tar.gz


cd libmtp-0.0.21/


./configure --prefix=/usr
sudo make
sudo checkinstall
```

Note: You _may_ have to run a --force-all dpkg on the created deb if it doesn't install right the first time.

```
sudo cp libmtp.rules /etc/udev/rules.d/


sudo /etc/init.d/udev restart
```


Once that's done, _then_ you can either do an upgrade to Feisty, or build Amarok, or whatnot. :) (of course you can upgrade first and do this after, but I just preferred to do it like this)

---

### Post by Rodneyck on 2006-12-03
I have not made the transistion to Fiesty yet. I may wait until they officially release it, maybe. ;) 

What I will do is bookmark your suggestions for the future. This gives me hope. I use gnomad2 like all the others, but it would be great to get it working with Amarok.  Thanks so much!!!

---

### Post by roger99 on 2006-12-05
I'm not having any luck with my Creative Zen Touch and amarok.  I've tried using debs from this guide [http://evolvedlight.co.uk/?p=13](http://evolvedlight.co.uk/?p=13) using libmtp2.0.0.18-0 from edgy's repo's with no luck.

Mtp-detect discovers the hardware but no mtp plugin in amarok.  I've just removed libmtp2.0.0.18 from the repos and installed libmtp-0.0.21 from the sourceforge link in this thread and again it works but amarok still has no option for mtp.  Which leads me to think the version of Amarok in imbrandon's repo's doesn't actually contain mtp support like claimed.

Is building Amarok from source a challenge, can anyone give me any pointers on how to build for Edgy with mtp support?

Any help will be appreciated! :confused:

---

### Post by ButteBlues on 2006-12-05
Again, under feisty - not edgy.


You'll need to build libmtp 0.0.21 from source.


Then, you can, if you want, build amarok. Just add the --with-njb and --with-mtp flags.

---

### Post by roger99 on 2006-12-05
Hi, thanks for the reply, i've just tried compiling the svn version of amarok and this is probably a complete noob question, but the configure script is asking for the path to the X libs. i've looked around my system but i'm not entirely sure what the correct path is.

Should I be looking under /usr or somewhere else?

---

### Post by ButteBlues on 2006-12-05
```
sudo apt-get build-dep amarok
cd /path/to/amarok/svn
./configure --with-njb --with-mtp --prefix=`kde-config --prefix`
make
sudo make install
```

---

### Post by roger99 on 2006-12-06
Thank you very, very much a simple façade, I now have Amarok with mtp support, my zen is recognized and everything works as it should.  Although I did have to use

```
--with-libnjb --with-libmtp
```

as options for the latest configure script.

I'm now a lot more confident with compiling source than I was last night :D

One other question as I'm still learning here, using apt-get build-dep *****, I presume the source in question has to have a package in the repo's so apt-get knows it's build dependencies.  Is that correct?

and once again cheers!

---

### Post by ButteBlues on 2006-12-06
I'm not 100% sure, but I do believe that is correct.

---

### Post by Rodneyck on 2006-12-06
Two questions...

1. Roger99, did you upgrade to Feisty or are you doing this on Edgy?

2. I am a complete noob when it comes to compiling. Is there anyway you can sum all that up into an easy step guide?  It is sort of jumbled if you read through the thread, at least from a noobs perspective.

Best..

---

### Post by ButteBlues on 2006-12-06
Rodneyck: Follow these instructions.


1. Run the following commands:

```
cd ~
mkdir amarok-with-mtp
cd amarok-with-mtp/
```

2. Save this file to ~/amarok-with-mtp: [link](http://prdownloads.sourceforge.net/libmtp/libmtp-0.0.21.tar.gz?download).

3. Run the following commands:

```
sudo apt-get update
sudo apt-get install libnjb
tar -zxvf libmtp-0.0.21.tar.gz
cd libmtp-0.0.21
./configure --prefix=/usr
sudo make
sudo checkinstall
cd ../
```

4. Save this file to ~/amarok-with-mtp: [link](http://mirror.cc.columbia.edu/pub/software/kde/stable/amarok/1.4.4/src/amarok-1.4.4.tar.bz2).

5. Run the following commands:

```
tar -jxvf amarok-1.4.4.tar.bz2
cd amarok-1.4.4
sudo apt-get build-dep amarok
sudo apt-get install libxine-extracodecs
./configure --with-njb --with-mtp --prefix=`kde-config --prefix`
make
sudo make install
```

6. Restart the X server or your PC, and then load Amarok. Connect your Creative MTP device to the computer.

7. Your MTP player should be detected by default in Amarok. If not, go to Tools > Configure Amarok > Media Devices and run AutoDetect, or add an MTP Device.

---

### Post by roger99 on 2006-12-06
> **Rodneyck said:**
> Two questions...

1. Roger99, did you upgrade to Feisty or are you doing this on Edgy?



Yes, I have done this on Edgy and I think facade answered the other question plenty well enough for me to leave it at that  :p 

Amarok works a treat now!

---

### Post by Rodneyck on 2006-12-06
Well thanks guys. Everything installed correctly and when I go to set the device it does actually read my Zen Micro player, changing the generic NJP naming to "Creative Zen Micro" in Amarok. The player shows it is communicating but in the middle of it, I get an error saying something about not having Kmail installed, which I do not, then it crashes after clicking on the OK button.

I would bet it is trying to send an error report. So, unfortunately, it does not work with my player. *sigh* Oh well, back to gnomad2.

Great effort though and this should probably be a sticky.

---

### Post by ButteBlues on 2006-12-06
I would recommend reinstalling Amarok if that's your issue. :)


It's just having a simple bug crash.



You could use the packages located here [amarok deb](http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok_1.4.4-0.3ubuntu2_i386.deb) and [amarok-xine deb](http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/amarok-xine_1.4.4-0.3ubuntu2_i386.deb).


In fact, I think I shall write a bash script for this. :)

---

### Post by Rodneyck on 2006-12-06
Actually, I just rebooted my computer completely. Before I just logged out to restart the X server, and now it is working. Very good!!!  

Thanks a lot, that was very easy to follow instructions.

---

### Post by ButteBlues on 2006-12-06
Here is version 1.0 of my bash script. :)

---

### Post by emmabulpit on 2007-08-11
Hi first time Ubuntu user and might be silly question but where do I put the code?

---

### Post by rajan on 2007-08-28
Emmabulpit,
 it doesn't really matter where you put the script because it uses the cd (change directory) command to get into the right one on its own. If I were to use this script I would create a new directory in your home folder and name it downloads or something. Then you can put it in there and run it. Click "run from terminal" if you are asked.

---

### Post by Qharos on 2008-02-02
I ran the script but wound up with the following errors:

....
```
Setting up directories.
Now downloading the required files.n
./amarok-with-mtp: line 56: unexpected EOF while looking for matching `"'
./amarok-with-mtp: line 58: syntax error: unexpected end of file
```

The last line in the file (57) is simply: "fi"

---

### Post by rajan on 2008-02-02
"fi" is how you end a conditional statement in shell scripting. in other words, it's supposed to be there.

---

### Post by Qharos on 2008-02-02
> **rajan said:**
> "fi" is how you end a conditional statement in shell scripting. in other words, it's supposed to be there.

Okay, so I learned a new thing. :) Scratch that part, then. The rest still doesn't work, though. :/

---

### Post by rajan on 2008-02-03
took a look at this, and i think the problem is that the script is missing the closing quotation mark on line 23. instead of 

```
echo "Retreiving amarok debian packages.
```

it should be 
```

echo "Retreiving amarok debian packages."
```

I'm not sure how you're running the script (or your level of computer usage), but I would open this file with a text editor and insert that quotation mark and then run it again.

In the future if you're hoping to diagnose your own problems (which I think everyone on this board is), I suggest you use emacs as a text editor. The reason I say that is that there is a feature called "syntax highlighting" that will change colors of the text depending on what is typed. try it out and see what i'm talking about. in fact if you use it while you are editing the script as i suggested above, you should see the color-change difference when you correct the problem.

maybe it's a good idea to send a private message to ButteBlues because it seems he's not monitoring this thread anymore. hope this helps,

rajan

---

### Post by cdude on 2008-03-24
Here is a Solution -  I am using Hardy with Rhythmbox 0.11.5, but I suppose the same would be true for Gutsy. 

Install **libmtp7**:

```
sudo apt-get install libmtp7
```

Then in Rythmbox enable the **Portable Players - MTP** plug-in 

Thant's it ;)

---

### Post by Ghost|BTFH on 2008-03-26
That would work awesome if Gutsy was ready for libmtp7, it's got 6, and installing 7 is a conga-line of deps required.

---

### Post by BigGeoff on 2008-03-29
I have just tried this and all I can get is 'cannot find package' - should I be updating my sources list to get this?

Geoff

---

### Post by Ghost|BTFH on 2008-03-29
Just an update: This is how to get it to work.

#1: Just make sure you install gnomad2.

#2: Run gnomad2 as root (Unless you're smart and know how to change ownership of the USB drives, that is...which mine seemed to start working after I manually started hald up, which for some reason wasn't running...so if you have an issue using it under normal user, checked to see if hald is up and running or not.)

#3: Enjoy using the player. :)

Now, if anyone knows how to convert video files to a format that the Zen V Plus will read properly, I'd love to hear it. :)

Cheers,
Ghost|BTFH

---

