---
title: "HOWTO: Buy MP3 music from Amazon.com."
date: 2008-08-05
forum: Multimedia Software
---

### Post by bcrowell on 2008-08-05
**How amazon's system works**

Typically if you search for MP3 files on amazon, you'll get a list of matching tracks with "Buy MP3" buttons, and also possibly some albums with buttons that say "Buy MP3 Album." (See the first screenshot attachment below.) It doesn't matter whether you have 1-click ordering turned on or not; if you're logged in, clicking on the orange button immediately charges your credit card and starts downloading the music.

Amazon has two separate mechanisms for downloading music. If you buy an individual track, and haven't installed any of amazon's special software, your browser simply downloads it as an MP3 file. However, if you want to buy an entire album, you have to install a special downloader application provided by amazon; your browser downloads a small file in .amz format, which you then have to open with the downloader in order to get the actual MP3 tracks of the album. (See the second screenshot attachment below.)

As of August 2008, some users are getting individual tracks -- not just albums -- downloaded via amz, while other users are still seeing them downloaded directly as mp3 files. It appears that this depends on whether you have your browser configured to use the downloader for albums: [http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154230](http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154230) Apparently if you've installed the downloader and configured your browser to use it for albums, then the downloader will also automatically be used for individual tracks as well, without the option of directly downloading an mp3.

For Windows and Mac users, the advantage of the downloader application is supposed to be that it integrates with iTunes or Windows Media Player. It also handles things like resuming interrupted or failed downloads. There is a Linux version of the downloader, and this howto is about solving common problems with getting it to work.

If you buy an album without having the downloader installed on your system, your browser will detect that, and will detect that you're running Linux, and it will offer you links to download various Linux versions of the software. Unfortunately the downloader isn't open-source, so you're limited to the binary versions that amazon provides, and it may be difficult to get these working if you're using a later version of Ubuntu than they anticipated, or if you're on a different architecture, such as a 64-bit machine. One of the frustrating things about trying to get it to work on my x64 machine has been that Amazon's tech support people have consistently insisted (on three different calls) that Linux is not supported, even though their own web site states that Linux is supported: [http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154260](http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154260) . The same web page also states that "is compatible with the most commonly used Web browsers," but I've also had a tech insist that it would not work with Firefox. 

Currently only U.S. customers can buy music on Amazon: [http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154210](http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154210) .

Amazon's terms of use say that they're not actually selling you the music, they're just selling you a license to use it: [http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154280](http://www.amazon.com/gp/help/customer/display.html?ie=UTF8&nodeId=200154280) However, the terms of use are fairly permissive. They say they're only selling you the right to download it once, and if you accidentally delete the file, you're out of luck.

**Clamz**

One way to bypass the problems with amazon's downloader is to use an alternative, open-source downloader written by Benjamin Moody, called clamz: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/) It's a command-line program.

To install clamz, click on the link to download clamz-0.2.tar.gz, save it into a directory where you want to work, open a terminal window, and cd into that directory. In the terminal window:

The documentation for clamz says to install the necessary libraries like this:

```
sudo apt-get install libgcrypt11-dev libcurl4-gnutls-dev libcurl4-openssl-dev libexpat1-dev
```

On my system, however, libcurl4-gnutls-dev didn't want to install, so I did this instead:

```
sudo apt-get install libgcrypt11-dev libcurl4-openssl-dev libcurl4-openssl-dev libexpat1-dev
```

Next you have to compile and install clamz:

```

tar -zxf clamz-0.1.tar.gz
cd clamz-0.1
./configure && make
sudo make install

```

Now if you click to buy a song, your browser will offer you a download dialog. Save the .amz file to disk. Next, from the terminal use clamz to download the actual MP3(s):

```

clamz 01\ -\ Better\ Git\ It\ In\ Your\ Soul\ -\ Antibes\ 1960\ -\ Live.amz

```

To avoid having to type the extremely long filename, you can just type the first few characters, then hit the tab key, and your shell should supply the rest of the filename.

As of October 2008, it looks like version 0.1 of clamz no longer works. Make sure to upgrade to 0.2.

**The amazon downloader -- 32-bit machines**
If you prefer to use the amazon downloader, here's how it's supposed to work. From the links supplied on the amazon page that came up after you bought your song, select the .deb file that most closely approximates the version of Ubuntu you're using. Open a terminal window, cd into the directory where you downloaded the .deb file, and do the following:

```

sudo apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
sudo dpkg -i amazonmp3.deb
amazonmp3

```

The third line is to test whether the program will actually run. It should start up the downloader's GUI.

Although you've installed the downloader, your browser won't automatically detect that fact. When you buy a song, you'll get a web page with an error saying that you need to install the downloader. Way down at the bottom of that page, however, you'll get a very small message saying, "If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser." You have to click on that the first time in order to make downloads work. I've sometimes observed that the error message recurs even after you've gone through this step to configure your browser. I think this may be because it uses a cookie to remember the configuration, so if you clear your cookies, you have to do it again.

For convenience, you'll probably want to configure your browser so that it automatically associates the filetype .amz with the amazon downloader. Here's how to do that in Firefox. When you buy your first song, you'll get a dialog box saying "You have chosen to open foo.amz ... What should Firefox do with this file?" Choose "Open with" "Other...", and in the dialog box that pops up, choose /usr/bin/amazonmp3. Then check the box that says "Do this automatically for files like this from now on." To change this file association later, go to Edit>Preferences>Applications>AmazonMP3 download queue.

**The amazon downloader -- 64-bit machines**

On a 64-bit machine, the method above may not work, because amazon only supplies the downloader as a 32-bit application, which needs 32-bit libraries. In this case, if you run the amazonmp3 program from a terminal window, you'll get an error message something like this:

```
amazonmp3: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
```

There is a script called getlibs that's designed to help you get around this problem: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790) The 32-bit instructions above have to be modified like this:

```

sudo apt-get install libboost-signals1.34.1 libboost-iostreams1.34.1
sudo dpkg -i --force-all amazonmp3.deb
which amazonmp3
getlibs /usr/bin/amazonmp3
apt-get install lib32nss-mdns
amazonmp3

```

The line to install lib32nss-mdns is necessary in order to get rid of a mysterious-seeming error. If you don't have this package installed, then every time you try to use the downloader you'll get messages saying "Can't connect. Please check your internet connection..."

BFris reports that having ipv6 networking enabled will also cause the downloader to fail: [http://ubuntuforums.org/showthread.php?t=777780](http://ubuntuforums.org/showthread.php?t=777780) .

**Other problems**
I've seen the following problem reported by other people, but haven't encountered it myself. It may be a bug that amazon has already fixed. The bug is that when you download a .amz file, your browser puts it in /tmp and makes it read-only. Then when the downloader app tries to open it, the first thing it does is try to delete it (so that it won't be left behind when the process is complete). This fails because the file is read-only, and the downloader then fails without any informative error message.

**Redoing a download after having a problem**
If you've had a problem with a download and want to retry it, you have a couple of options.

One method is simply to start amazonmp3 again from the command line (rather than from your browser). It should retry any downloads that are still outstanding.

If you prefer clamz, or can't get amazonmp3 to work, you can also go to the amazon web site, move your mouse over the down-arrow next to "Your lists" (don't click on the words "Your lists," which will do something different), then click on "Your media library." Hover your mouse over the down-arrow in the "Downloads" tab, and click on "Amazon MP3." If you click on the underlined link for a particular song or album, it will give you some information about the track, such as when you bought it, and whether you've already downloaded it. If you click on the Download button on the right, it should let you download it. (If it thinks you've already completed the download, it won't let you download it again.)

**Technical information about the .amz format**
A .amz file is an XML file that's encrypted using DES, in CBC mode, and written in base64 format. The DES key is 29AB9D18B2449E31. The initialization value for CBC is 5E72D79A11B34FEE. For more information about the format, see the source code to clamz. I don't understand the point of the encryption, since no effort seems to have been made to keep the keys secret, and having an amz file won't do you any good if you don't have the login information for the account of the person who paid for it.

**"Deluxe" albums**
Some albums include other materials besides mp3 files, such as liner notes or videos. When you try to download one of these, amazon's web interface will tell you that you need to install the downloader. It doesn't help if you click on the link saying "If you have already installed the Amazon MP3 Downloader, click here to enable it for use with this browser." Instead what you have to do is set a certain cookie manually. To do this, go to the amazon.com home page, and type the following in the URL bar of your browser:
```
javascript:document.cookie='dmusic_download_manager_enabled=1.0.9;expires=Fri, 21 Dec 2012 12:00:00 UTC; path=/; domain=.amazon.com'
```
The version number 1.0.9 is what works as of October 2010. In the future you may have to increase this.

---

### Post by MichiganMan on 2008-08-09
> **bcrowell said:**
> **How amazon's system works**



Recently (August 2008), however, amazon seems to have changed their system so that all downloads go through the .amz step, even if you're just buying an individual track.
Horrified after reading this, I went to try to purchase an individual track, (Damaged by Danity Kane (girlfriends choice ;))) It downloaded as an intact mp3, just like before.

---

### Post by bcrowell on 2008-08-09
> **MichiganMan said:**
> Horrified after reading this, I went to try to purchase an individual track, (Damaged by Danity Kane (girlfriends choice ;))) It downloaded as an intact mp3, just like before.

Interesting. As a test, I bought the same song, and it downloaded it as an amz, not an mp3. Based on our data, and on some info on amazon's help pages, it looks like they've changed their servers' behavior so that if you've configured your browser to use the downloader for albums, it will also use it for individual tracks. I've edited the howto to explain this.

---

### Post by bcrowell on 2012-07-25
For those who prefer to use Amazon's GUI downloader for albums, here's a howto someone wrote on how to get it running on a recent version of ubuntu:[http://helpdeskgeek.com/linux-tips/get-the-amazon-mp3-downloader-working-in-ubuntu-11-10/](http://helpdeskgeek.com/linux-tips/get-the-amazon-mp3-downloader-working-in-ubuntu-11-10/)

---

### Post by wildmanne39 on 2012-07-25
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

