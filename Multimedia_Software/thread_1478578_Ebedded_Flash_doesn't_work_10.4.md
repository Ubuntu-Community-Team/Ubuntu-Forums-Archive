---
title: "Ebedded Flash doesn't work 10.4"
date: 2010-05-09
forum: Multimedia Software
---

### Post by acrotwell on 2010-05-09
I've searched and nothing like what I'm experiencing.  New install of 10.4. Flash works for Youtube, but when I try to view embedded flash like on engadget or something, I just get a static image with a big "play" button, but nothing happens when I click on it.  I can right click and play in Youtube, but even then, the play/pause button doesn't work.  Also, on my own site the flash doesn't play, just a static image [www.reedmason.com](www.reedmason.com).  

I've installed the latest Flash player from Adobe, I've tried the repositories, I've tried the .so manual install. Nothing so far.....

Any help would be greatly appreciated.

64bit.

Worked in 9.10

---

### Post by WinterRain on 2010-05-09
> **acrotwell said:**
> Also, on my own site the flash doesn't play, just a static image [www.reedmason.com](www.reedmason.com).  

I've tried the .so manual install.

Which manual method did you try? Btw, your site works fine for me, and I'm using 64bit.

Try manual one more time.

Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

---

### Post by acrotwell on 2010-05-10
With the help of a friend, I got the 64bit version to work using the correct package.

add the source:
sudo add-apt-repository ppa:sevenmachines/flash

Then update the repository listing:
sudo apt-get update

Install the 64 bit flash plugin:
sudo apt-get install flashplugin64-nonfree

Thanks to those that replied. I love the community!

---

### Post by CMTegner on 2010-07-16
Thanks for the tip acrotwell, that guide almost worked 100% for me (on 10.4/64bit)! The only difference was that I couldn't find the flashplugin64-nonfree package in the repo you specified, I had to use flashplugin64-installer instead. After that embedded flash worked fine!

Another thing I noticed (before I switched to flashplugin64) was that some youtube video settings weren't working, for example changing resolution. There may be a link between this and the buttons on the embedded player not working.

---

### Post by sunshine316 on 2010-07-19
so in short the new steps are 
1)add the source:
sudo add-apt-repository ppa:sevenmachines/flash

2)Then update the repository listing:
sudo apt-get update

3)Install the 64 bit flash plugin:
sudo apt-get install flashplugin64-installer

thanks for the help everyone

---

### Post by Digicraft on 2010-08-05
I found that after doing all that is suggested earlier, Flash audio suddenly worked but general audio then failed after having worked before, and I got a message indicating that my Audigy SE card no longer worked. When I booted into Windows, sound no longer worked there either. I booted back into Ubuntu 10.4 and uninstalled the 64-bit Flash installer that I had just installed. Using Synaptic, I then re-installed the original flash installer and plugin-nonfree, and all works great now. I played a Youtube video and, when over, I brought up VLC whose audio failed until I closed the (now idle) Youtube page. That was interesting but livable, and I appear to be in business thanks to everyone's advice here, though I haven't been back to Windows yet. Sound is still a time-consuming pain in Ubuntu I'm afraid. That's a biggee.

---

### Post by jettechfsr on 2010-08-11
Thanks for the help my triple boot Macbook 7,1 is getting better everyday i'm going to have to figure out how to put Ubuntu icon in rEFit first :p

---

### Post by Yellow Pasque on 2010-08-11
64-bit Flash is dead. You can use the old one, but there are known security vulnerabilities (so use Flashblock or NoScript if you must use it).

The OP (using 32-bit Flash and nspluginwrapper) probably could have fixed his issue with this little tweak: [http://ubuntuforums.org/showpost.php?p=9529549&postcount=230](http://ubuntuforums.org/showpost.php?p=9529549&postcount=230)

---

