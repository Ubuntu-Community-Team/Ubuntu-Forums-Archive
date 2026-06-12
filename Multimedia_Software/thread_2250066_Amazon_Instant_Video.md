---
title: "Amazon Instant Video"
date: 2014-10-26
forum: Multimedia Software
---

### Post by tray2 on 2014-10-26
Hi caffeinatedev:

I've been struggling to get Amazon Prime Video to play using Chrome and Firefox, neither works. I'm using Lubuntu 14.04. When I ran the code suggested in your post it didn't work; here's what I got:

sudo apt-get install hal
[sudo] password for ray:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package hal

I'm a Lubuntu Newbie, perhaps I'm just dense, but I can't seem to figure this out... can you offer any advice?

Thanks in advance!
RT

---

### Post by coffeecat on 2014-10-26
Welcome to the forum!

You posted to a nearly 2-year old thread, where the person you are addressing has not logged in for months and where most of the posts refer to now-obsolete versions of Ubuntu. People are less likely to post to old threads, and the posted fixes may or may not be relevant to the current 14.04 release. Better to start afresh. I've moved your post out into its own thread.

Good luck in finding a solution.

---

### Post by Adrian Nania on 2014-11-27
try to install hal-flash from here: [https://launchpad.net/~mjblenner/+archive/ubuntu/hal-flash](https://launchpad.net/~mjblenner/+archive/ubuntu/hal-flash)
#          this info was from: [http://www.youtube.com/watch?v=dMM_Bqsg6Ps](http://www.youtube.com/watch?v=dMM_Bqsg6Ps)
or check this post: [http://ubuntuforums.org/showthread.php?t=2232122&highlight=amazon+prime+video](http://ubuntuforums.org/showthread.php?t=2232122&highlight=amazon+prime+video)

---

### Post by SeijiSensei on 2014-11-27
There's a long thread about this issue at Amazon's forums.  Read [this posting](http://www.amazon.com/forum/amazon%20video%20on%20demand/ref=cm_cd_et_md_pl?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cdMsgID=Mx1UABVBN1RCMO3&cdMsgNo=183&cdPage=8&cdSort=oldest&cdThread=Tx167YET6CH0PQI#Mx1UABVBN1RCMO3) to begin.

---

### Post by Adrian Nania on 2014-11-28
Dear RT, I've got pretty tired to skim trough thousands of posts just to see all of them failing. Here is what worked for me, using Mint 17 and Kubuntu 14.04
The first way is to install wine and after that the latest version of Mozilla Firefox and Adobe Flash player:
```

# watch amazon videos in linux (WORKING)
sudo apt-get install -y wine winetricks playonlinux # you can skip winetricks and playonlinux packages
cd /home/work/src/media/FlashPlayer # or use your own local folder for this kind of data
# download the latest firefox as of today 20141128:
wget https://download.mozilla.org/?product=firefox-33.1.1-SSL&os=win&lang=en-US
mv ./index.html?product=firefox-33.1.1-SSL ./firefox.exe
wine ./firefox.exe
# download the latest Windows 7 flash player with no ActiveX from Adobe, as of today 20141128
# from: http://get.adobe.com/flashplayer/otherversions/
# step 1: [Windows 7/VISTA/XP/2008/2003]
# Step 2: [FP 15 for Firefox - NPAPI]
wget http://fpdownload.macromedia.com/get/flashplayer/pdc/15.0.0.239/install_flash_player.exe
wine ./install_flash_player.exe
# now start the wine/window$ version of Firefox

```
The second way is to install and use pipelight:
```

# watch amazon videos in linux (WORKING)
# to play Amazon video, from: http://pipelight.net/cms/installation.html
# install the package for your distro (ubuntu)
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get -y autoclean
sudo apt-get -y autoremove
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
# activate plugins
sudo pipelight-plugin --enable silverlight
sudo pipelight-plugin --enable flash
sudo pipelight-plugin --unlock shockwave
sudo pipelight-plugin --enable shockwave
sudo pipelight-plugin --enable unity3d
sudo pipelight-plugin --enable widevine
# now just start the default Linux Firefox

```
I tried VERY hard to have HAL working again but this stuff looks like just died:
```

# watch amazon videos in linux (NOT WORKING)
# install HAL from: http://forums.linuxmint.com/viewtopic.php?f=47&t=174619 (NOT WORKING)
sudo add-apt-repository ppa:mjblenner/ppa-hal
sudo apt-get update
sudo apt-get install hal
# install libhal and start haldaemon, from: www.amazon.com/forum/amazon video on demand?_encoding=UTF8&cdForum=Fx3EQAX98ED5WQ3&cd
# from: http://alexsantidote.com/866/how-to-watch-amazon-prime-videos-in-ubuntu-14-04/ (I tried to dwnload the deb packages and install them one by one)
#            cd /home/work/src/drivers/HAL/
#            sudo dpkg -i ./hal-info_20091130-1_all.deb ./libhal-storage1_0.5.14-8_amd64.deb ./libhal1_0.5.14-8_amd64.deb ./hal_0.5.14-8_amd64.deb
sudo mkdir /etc/hal/fdi/preprobe
sudo mkdir /etc/hal/fdi/information
/usr/sbin/hald --daemon=yes --verbose=yes
rm -rf ~/.adobe
pstree # no HAL daemon visible here

```
And finally, Google Chrome NEVER worked, with or without pepperflash:
```

# watch amazon videos in linux (NOT WORKING)
# install google chrome, from: http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line
sudo apt-get install -y libxss1 libappindicator1 libindicator7
cd /home/work/tmp
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome*.deb
# from: http://www.webupd8.org/2014/04/10-things-to-do-after-installing-ubuntu.html
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install

```
I would appreciate if somebody can show me what I am doing wrong, how to activate HAL and how to set Google Chrome to play Amazon videos

---

### Post by monkeybrain20122 on 2014-11-29
Chrome may have up to date flash but it is not drm capable, so pepperflash won't work. If hal doesn't work maybe pipelight-flash is your only hope. I don't watch Amazon videos so that is all I can say on the topic.

---

### Post by three-legged_dog on 2014-12-11
For anyone who is really new like me.  After installing Pipelight I had trouble figuring how to agree to the license agreement. if you press tab and enter it lets you agree.  
Adran Nania Thank you for your helpfull post.

---

