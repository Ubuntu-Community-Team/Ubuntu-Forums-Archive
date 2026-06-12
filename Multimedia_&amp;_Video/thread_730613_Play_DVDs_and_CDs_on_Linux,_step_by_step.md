---
title: "Play DVDs and CDs on Linux, step by step"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by asilaydyingdl on 2008-03-21
After much time, research, and effort, I now have full CD and DVD capabilities on Xubuntu Linux. Here are the steps I went through to achieve this for anyone else who has had difficulty. Make sure you have an internet connection on your computer to do this!

1. Using the Synaptic Package Manager, install Kaffeine media player (I recommend this app after using other media players), libxine 1-x, and avifile-win32-plugin. This should give you CD capabilities pending you already have xubuntu/ubuntu restricted extras installed. If not, install that package as well. To locate these items quickly, use the search feature found on the Synaptic's toolbar.

2. Go to applications>Accessories>Terminal or the location of your Terminal. Open terminal, and paste and run the appropriate codes from the following web page in it. Make sure after you run the appropriate command for your computer.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

To finish make sure you paste this code into terminal and run it, in case you didn't see this code on the web page. If you already ran it once, then ignore this:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

That updates the newly added repository.  Copy and paste that  entire line, the link wont hurt anything.

3. Paste the following code into terminal and run.

sudo apt-get install libdvdcss2 libdvdnav4 lsdvd libdvdread3 libavcodec1d non-free-codecs

And that should be it! Open up Kaffeine and try a CD or DVD. If Kaffeine gives you some sort of error message the first time you open it, ignore it. I had it and have not had any trouble whatsoever with the application. Some DVDs may freeze up as they play the short clip that usually leads into the main menu, so I find it best to just skip ahead to the main menu. After that I have no trouble playing the DVD. This may not be the case for you, my DVD drive may just be moody. Have fun!

---

### Post by Sturch001 on 2008-03-21
Hello

I'm having some trouble installing Kaffeine.

After I extract the files and run 

  ./configure

I end up with this error:

  checking for C compiler default output file name... configure: error: C compiler cannot create executables


What am I doing wrong?

---

### Post by JudgeFudge on 2008-03-22
> **Sturch001 said:**
> Hello

I'm having some trouble installing Kaffeine.

After I extract the files and run 

  ./configure

I end up with this error:

  checking for C compiler default output file name... configure: error: C compiler cannot create executables


What am I doing wrong?

Did you try running "sudo apt-get install kaffeine" from the terminal.

---

### Post by xc3RnbFO8P on 2008-03-22
> **Sturch001 said:**
> Hello

I'm having some trouble installing Kaffeine.

After I extract the files and run 

  ./configure

I end up with this error:

  checking for C compiler default output file name... configure: error: C compiler cannot create executables


What am I doing wrong?

You need this:
> sudo aptitude update
sudo aptitude install build-essential

---

### Post by 512mattw on 2008-03-24
I have a gateway gt5654 and am able to play dvds but not cds. There is only one optical drive and its a dvdrw.
when cd is entered it brings up on the desktop "CD-ROM disk" in banshee it recognizes "new audio cd" and the length of the cd but not the artists.  I am un able to play disk with any software.

please help
new to Ubuntu

---

