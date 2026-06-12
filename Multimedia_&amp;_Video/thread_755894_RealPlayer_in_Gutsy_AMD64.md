---
title: "RealPlayer in Gutsy AMD64"
date: 2008-04-15
forum: Multimedia &amp; Video
---

### Post by Jimmy9pints on 2008-04-15
I know there are a lot of posts about this but despite working through a lot of the methods I still haven't got an answer. I have been listening to BBC Radio 4 almost everyday for almost my whole life - now I can't.

I am running Ubuntu Gutsy AMD64 and I can't install RealPlayer! No radio 4 is like torture for me! Please help.

---

### Post by warp99 on 2008-04-15
You can use the mplayer mozilla plugins to listen to realplayer audio if you have mplayer installed or you can use the 32-bit version from realplayer since it works fine on 64-bit Gusty.

Edit:
With realplayer you have to open the link in a separate player window, not embedded.

---

### Post by Jimmy9pints on 2008-04-15
Thank you for your reply! I have been working on this problem for weeks without success.

I have m-player installed. Originally this worked after a fashion but streaming was extremely erratic! It stopped and started al the time and when it restarted the volume was extremely LOUD and distorted.

So I started looking for RealPlayer (althouhgh I used realalternative on windows). I followed instructions in many different posts. Basically trying to install the .bin I got the "no such file or folder" error. And with the .deb the error was that it only supported i386 achitechture (i.e. not my AMD64).

I found an article on Ubuntu wiki about installing 32bit Firefox plugins. [https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava]("https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins?action=show&redirect=FirefoxAMD64FlashJava")

Please tell me what's the best way to solve this problem.

---

### Post by warp99 on 2008-04-15
I've been using 64-bit Ubuntu since Breezy (5.10) so I know a little about the frustration with 32-bit plugins. The best way I found is to remove the 64-bit install of Firefox and install the 32-bit version direct from Mozilla which allows me to use all of the 32-bit plugins available, such as native Adobe Flash and Adobe Reader. The 32-bit version runs fine on the 64-bit install except for some minor issues with using Adobe Acrobat Reader's online tools, but there is a workaround if you really need them.

If you don't want to install a 32-bit browser right now another way is to use your 64-bit browser and have most multimedia plugins work by using a Firefox extension called MediaPlayerConnectivity:

[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

Now with this extension you can launch external applications easily with embedded media including BBC radio. If you want BBC radio you can use this extension with Realplayer and it works with no problems. I can help you install Realplayer and have it run system-wide, it's very simple:

Download the bin file here:

[http://www.real.com/linux/?pageid=unagi.17735126.wrapper&pageregion=footer&src=realplayer_com&pcode=rn&opage=realplayer_com](http://www.real.com/linux/?pageid=unagi.17735126.wrapper&pageregion=footer&src=realplayer_com&pcode=rn&opage=realplayer_com)

go to the directory the file is in, then change the permissions of the file to execute:
```
chmod 775 RealPlayer11GOLD.bin
```
now execute the file as root using 'sudo':
```
sudo ./RealPlayer11GOLD.bin
```
the installer will extract and ask some questions:
```
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/opt/real/RealPlayer]:

```
use the directory '/usr/local/realplayer' since this is where local files are normally placed for Debian based installations:
```
You have selected the following RealPlayer configuration:

Destination:            /usr/local/realplayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]:

```
the program starts to install the files complete with menu entries. Realplayer will also find your /usr/lib/mozilla/plugins and install some web plugins, but they will not work because you have a 64-bit browser. Now there is one more thing you need to do and that is place a symlink to the replayer bin file:
```
sudo ln -s /usr/local/realplayer/realplay /usr/local/bin/realplay
```
this will allow realplayer to be launched system-wide by just entering 'realplay'.

Now how do we play the real embedded webfiles with Realplayer? That's were the MediaPlayerConnectivity Firefox extension comes into play. Set the extension to call the bin file '/usr/local/realplayer/realplay' and when you click on a real embedded link the file will open in realplayer.

---

### Post by Jimmy9pints on 2008-04-16
Thanks Warp! 

I will try this as soon as I get home - (I am at work now using Windows)

I have tried the same and similar techniques before but when I got to  entering "sudo ./RealPlayer11GOLD.bin" it said there was no such file or folder. It was really annoying because I could see it there and I was sure I was in the right directory. 

Anyway...I will persist - failure is not an option.

---

### Post by warp99 on 2008-04-16
> **Jimmy9pints said:**
> Thanks Warp! 

I will try this as soon as I get home - (I am at work now using Windows)

I have tried the same and similar techniques before but when I got to  entering "sudo ./RealPlayer11GOLD.bin" it said there was no such file or folder. It was really annoying because I could see it there and I was sure I was in the right directory. 

Anyway...I will persist - failure is not an option.

The reason is because the file was not executable. The instructions that I gave include the string to make the file executable. Now the steps in the previous post is the actual output of a new install on my machine since I had an older version, so I know it works.

The only problem you may have is if you don't have ia32-libs it may not run, but if you've run 32-bit programs on your 64-bit machine in the past then they're already installed. If not the libraries are available in the universe respository under the name 'ia32-libs'.

---

### Post by Jimmy9pints on 2008-04-16
No end of thanks for this help! It's all working and I can listen to BBC radio again!

---

### Post by starfunker on 2008-04-26
Thank you, warp99; your instructions are helpful.  Unfortunately, I can't follow them to the end as the firefox extension hasn't yet been updated for Firefox 3.5.  I'll wait till it has and then try to finish.

---

