---
title: "Noob screwed something up..."
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by H3LlIoN on 2010-01-07
Moving this to new topic, since it's no longer under wireless connectivity issues...

[Noob Warning]

I was having trouble getting Ubuntu to recognize my wireless card, as I have changed from the 3965 that came in my computer to the 4965, which added increased range and G band.  Anyway, I read one of the threads on here, and this was the advice given:

> **pytheas22 said:**
> 

First, download [this file]("http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2") and save it to your desktop.  Then run these commands:

```
sudo apt-get install build-essential
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
tar -xzvf iwlwifi*
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
bunzip2 compat-wireless-old
tar xf compat-wireless-old
cd compat-wireless*old*
make
sudo make install
sudo make unload
sudo make load
```Now reboot. 

Prior to screwing around, I had perfect LAN connectivity, but was lacking in wireless, as my card was showing up as disable and inactive.  I tried this set of steps, and I got as far as line 4 (sudo cp iwlwifi...)  Up til that point, everything went like I am guessing it was supposed to.  Anyway, line 4 wouldn't do anything, and nothing else would work.  I restarted the computer, only to find that network manager appears to be gone, and I have no internet connectivity whatsoever at this point.  System/Admin/Network Tools shows that both of the cards are active now, but I have no connectivity, either through firefox, or any of the onboard ubuntu downloaders.  I can't copy/paste stuff, since the laptop doesn't have any obvious means of connectivity, but I can type it up, and I can post logs if you can tell me which ones to look in.  

Does anyone have any idea how to fix whatever I screwed up?

Thanks in advance

---

### Post by sanderd17 on 2010-01-07
I don't know what your problem is but I can help a little with explaining the code you used and maybe what is wrong with that code:

Install a package from the apt-get (this can also be installed trough synaptic)
```
sudo apt-get install build-essential
```
Download the file iwlwifi-5000-ucode-5.4.A.11.tar.gz to your current folder
```
wget http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-5.4.A.11.tar.gz
```
unpack the file you just downloaded
```
tar -xzvf iwlwifi*
```
copy the file sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode to /lib/firmware, 
```
sudo cp iwlwifi-5000-ucode-5.4.A.11/iwlwifi-5000-1.ucode /lib/firmware
```
unpack the file youi had to download manually, here it can go wrong if that file isn't in the directory you're working on. Try copying the file you downloaded manually to your home directory.
```
bunzip2 compat-wireless-old
```
The following command isn't correct, it should be 'tar -xf ...' but I bellieve you can skip this because it does just the same as the previous command.
```
tar xf compat-wireless-old
```
cd to the directory you've just unpacked
```
cd compat-wireless*old*
```
Excecute code to compile the package
```
make
sudo make install
sudo make unload
sudo make load
```

Hope I could help.

---

### Post by H3LlIoN on 2010-01-07
I made it to the copy the file to lib/firmware line, and the commands stopped working.  How about this...I have my harddrive partitioned between Karmic and XP Media Center...is there a way I can just overwrite the karmic partition with a fresh karmic install?  Going through the boot disc and trying to do this, it won't let me clean overwrite the currently installed instance of karmic; it will only let me make the partition really small (~5gb).  Ideally, I would like to not have to start over altogether, as it took me quite a while to delete all the crap that XP came packaged with...thanks for the info and help.

---

### Post by sanderd17 on 2010-01-07
If your installation is quite new, you can do a clean reïnstall.

Insert the live cd, dowload gparted and reformat your karmic partition. (**don't** reformat an ntfs partition because that will most likely be a windows partition). try to remember some info of the partition you reformated (like name "sda...", size, format "ext3 or ext4" ... ) to use in your installation proces.

Once reformated, retry to install karmic on that partition. Use it as "/" mount-piont.

---

### Post by H3LlIoN on 2010-01-07
Hold please...

---

### Post by H3LlIoN on 2010-01-07
Formatting now...what is the "swap" partition?

---

### Post by brusegadi on 2010-01-07
> **H3LlIoN said:**
> Formatting now...what is the &quot;swap&quot; partition?

 Its disc space that the operating system uses to free up RAM.  Check out:  [http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)

---

### Post by sanderd17 on 2010-01-07
the space for swap should be between your ram size and the double of your ram size

---

### Post by H3LlIoN on 2010-01-07
OIC.  Know what it is, but not used to the term.  This harddrive will do up to 16gb of "swap" space...if I configure that in XP does it carry over automatically to ubuntu?  


On the other note, gparted let me downsize and reformat the partition, but didn't completely get rid of it.  That being said, I'm reinstalling on a new partition, then gonna use gparted to delete original.  Thanks for the help, will let you know how it goes.

---

### Post by brusegadi on 2010-01-07
> **H3LlIoN said:**
> OIC.  Know what it is, but not used to the term.  This harddrive will do up to 16gb of &quot;swap&quot; space...if I configure that in XP does it carry over automatically to ubuntu?  


On the other note, gparted let me downsize and reformat the partition, but didn't completely get rid of it.  That being said, I'm reinstalling on a new partition, then gonna use gparted to delete original.  Thanks for the help, will let you know how it goes.

 So, there are at least two ways that paging can be done; on a partition separate from the main partition or on files written to the main partition.  My understanding is that the default windows install will do the latter, while the default Ubuntu install does the former.  So, the swap partition you encountered most likely belongs to Ubuntu.  If you are used to having many programs running at the same time, you probably want to have the recommended size for the swap partition.  Finally, check out     [https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)   GOOD LUCK!

---

### Post by H3LlIoN on 2010-01-07
This talks a little bit more about swap, and goes in to the differences between the different OS' utililization...  [http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

Now, I've heard twice now that the swap should be twice the RAM...does that mean I can realize no actual benefit by increasing it to more?

---

### Post by sanderd17 on 2010-01-07
you can only realize benifit if you run extremely large applications (extreme as in "I don't know any example"). But in that case you'll better buy something with a larger ram.

---

### Post by H3LlIoN on 2010-01-07
Hmmm wouldn't know what I would use like that in Ubuntu, but I do use some pretty serious stuff on the win side.  Does win/ubuntu use the same swap partition, or do they each create their own?  The only one that shows up on the drive is the ubuntu one, so I'm guessing win is separate and hidden...

---

### Post by sanderd17 on 2010-01-07
win doesn't support a swap partition. I've heard it uses swap files but I'm not sure.

---

### Post by H3LlIoN on 2010-01-07
It does, they just call it "paging."

---

### Post by H3LlIoN on 2010-01-07
Ubuntu back up and connected, thanks for the help.  Have to go back and reconfig, but shouldn't take long.

On a side note, tried using Gparted to delete old partition and swap, and it keeps telling me to unmount any partitions with a higher number.  Trying to do that though it says that it can't unmount because of multiple partitions on the same mount, and that I need to manually unmount.  No clue on that one, deal with it tomorrow.  Thanks for the help.

---

