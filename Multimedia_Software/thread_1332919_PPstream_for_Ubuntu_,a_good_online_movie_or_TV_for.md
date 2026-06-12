---
title: "PPstream for Ubuntu ,a good online movie or TV for you"
date: 2009-11-20
forum: Multimedia Software
---

### Post by cnzhuxi on 2009-11-20
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]i have good expierence the PPStream plugin for totem to wacth online TV or movie,so share with you and the installation as following

1,open terminal and copy code to add source list
                                                            > sudo gedit /etc/apt/sources.list2,then edit and add source list
>   [FONT=Arial]###PPS Totem [/FONT][FONT=Arial]PPA
deb [http://ppa.launchpad.net/portis25/ppa/ubuntu](http://ppa.launchpad.net/portis25/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/portis25/ppa/ubuntu](http://ppa.launchpad.net/portis25/ppa/ubuntu) karmic main[/FONT]
3,then update the suorce list and install totem-pps on terminal
                         > [FONT=Arial]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 27F5B2C1B3EAC8D9
sudo apt-get update
sudo apt-get install totem-pps[/FONT]
 4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list

to see the pic ,find this page
[http://tu.6.cn/pic/show-new/id/5432457/](http://tu.6.cn/pic/show-new/id/5432457/)
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]

---

### Post by schwim on 2009-11-20
Is this something that provides some kind of guide to find streaming content, or is it just a plugin that allows you to view streaming content that you find by other means?

---

### Post by cnzhuxi on 2009-11-20
to add this plugin for totem, we can wacth movie or TV online,

---

### Post by fcuk112 on 2009-11-21
Please ignore this post.

---

### Post by sunyiyang on 2009-11-22
Great!!!!

That's more useful than the official site.

thanks to share.

---

### Post by fcuk112 on 2009-11-23
This is awesome, thanks.  I have one issue though (see [http://code.google.com/p/totem-pps/issues/detail?id=3](http://code.google.com/p/totem-pps/issues/detail?id=3)).

What steps will reproduce the problem?
1. Goto chinese drama series.
2. Filter by &#23500;&#36149;&#38376; and select the cantonese version.
3. Try to play.

What is the expected output? What do you see instead?
It should play, instead I get an error message No URI handler implemented for "tvod".

What version of the product are you using? On what operating system?
I am using 0.0.18-1-i386 deb files on Ubuntu 9.10.

Does anyone have any idea how to resolve this?

Thanks.

---

### Post by dreampuzz on 2009-11-25
woah this is awesome ..

but somehow the loading of channels are damn slow compared to windows .. any ideas??

---

### Post by fcuk112 on 2009-11-28
never mind, i managed to resolve my issues by adding the PPA and removing/reinstalling totem-pps.

---

### Post by Hilko on 2009-12-16
Thanks very much. The plugin seems to be working. However, when i try to search for something i never find any results.
Is this because i type the keywords in English ? Should i type keywords in Chinese ? Or is there another problem ? 

There is a native linux version of ppstream. I found it here
[COLOR="Blue"][http://www.ppstream.com/download.html](http://www.ppstream.com/download.html)[/COLOR]
then click on the tab that says linux.

But i cannot get it installed. Does anyone know how to install it ? If you succeed, please post it here.

---

### Post by fcuk112 on 2009-12-16
I typed the keywords in Chinese.  The website 991881.com is also quite good, you can download the files to your PC and watch them using VLC or your favourite media player.

---

### Post by kevinwenyu on 2009-12-16
It's wonderful.i like it.

---

### Post by duongnn on 2009-12-19
> **cnzhuxi said:**
> 

                         4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list


I don't know how to open the totem. I can not find it in Applications.
Could you plz tell me how can I open the totem?

---

### Post by dreampuzz on 2009-12-19
> **duongnn said:**
> I don't know how to open the totem. I can not find it in Applications.
Could you plz tell me how can I open the totem?


configure plugin on the movie player

---

### Post by Hilko on 2009-12-20
> **duongnn said:**
> I don't know how to open the totem. I can not find it in Applications.
Could you plz tell me how can I open the totem?

Go to the menu on the top.
Applications -> Accessories -> Terminal
In the terminal type
```
totem
```

---

### Post by nghonyuen on 2009-12-26
Hi Guys:

Can i check if this method still work? I tried do the same thing for my ubuntu PC and it doesn't work.

After executing all the sudo commands, i open totem and enable PPS Browser. I manage to see the channels list. However, all list appear to be empty.

May i know if i did something wrong? Or PPS is closing support for linux? I no longer able to see the Linux tab in their official website.

Many Thanks,

---

### Post by ivylw on 2009-12-28
you should double-click the watchlist and it will update itself.

---

### Post by thongkh on 2009-12-28
> **nghonyuen said:**
> Hi Guys:
 
Can i check if this method still work? I tried do the same thing for my ubuntu PC and it doesn't work.
 
After executing all the sudo commands, i open totem and enable PPS Browser. I manage to see the channels list. However, all list appear to be empty.
 
May i know if i did something wrong? Or PPS is closing support for linux? I no longer able to see the Linux tab in their official website.
 
Many Thanks,
 
what u have now is normal, refer [http://code.google.com/p/totem-pps/issues/detail?id=6#c23](http://code.google.com/p/totem-pps/issues/detail?id=6#c23) for more details.

---

### Post by gordintoronto on 2010-03-28
> **cnzhuxi said:**
> [IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]i have good expierence the PPStream plugin for totem to wacth online TV or movie,so share with you and the installation as following

1,open terminal and copy code to add source list
                                                            2,then edit and add source list
3,then update the suorce list and install totem-pps on terminal
                         4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list

to see the pic ,find this page
[http://tu.6.cn/pic/show-new/id/5432457/](http://tu.6.cn/pic/show-new/id/5432457/)
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]

It appears that totem-pps has disappeared, and the other item in the thread has also gone away.  Can you shed any light on this?

---

### Post by Mauri72 on 2010-04-15
weird. it was working well up to about a week ago, but it seemed to have stopped altogether. Is anyone else experiencing this?

---

### Post by minijoe on 2010-04-15
Looks like PPStream is blocking access from 3rd party software again. It happened maybe they'll open it again later on.

---

### Post by bbiandov on 2010-04-15
it is NOT working for me?

I get the following error after the last apt-get:

```
boyan@BB20100305:~$ sudo apt-get install totem-pps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package totem-pps
boyan@BB20100305:~$ sudo gedit 

```

I just can't seem to get to the holly place:

[IMG]http://i3.6.cn/cvbnm/47/77/13/228ec8c35ff43c03f01bce1a6818df48.png[/IMG]

---

### Post by fipblizip on 2010-07-30
> **bbiandov said:**
> it is NOT working for me?

I get the following error after the last apt-get:

```
boyan@BB20100305:~$ sudo apt-get install totem-pps
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package totem-pps
boyan@BB20100305:~$ sudo gedit 

```I just can't seem to get to the holly place:


Try: [http://code.google.com/p/totem-pps/wiki/InstallGuideForUbuntu](http://code.google.com/p/totem-pps/wiki/InstallGuideForUbuntu)

---

### Post by 88300D on 2011-06-15
> **cnzhuxi said:**
> [IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]i have good expierence the PPStream plugin for totem to wacth online TV or movie,so share with you and the installation as following

1,open terminal and copy code to add source list
                                                            2,then edit and add source list
3,then update the suorce list and install totem-pps on terminal
                         4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list

to see the pic ,find this page
[http://tu.6.cn/pic/show-new/id/5432457/](http://tu.6.cn/pic/show-new/id/5432457/)
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]

Can i do this for ubuntu 11?
Peace and blessings Howie

---

### Post by Khakilang on 2011-06-15
Is it possible to install into 11.04. The source list I found is for 10.04. So how do I install into 11.04? Thanks in advance.

---

### Post by yuzhaoliang on 2011-06-24
> **Khakilang said:**
> Is it possible to install into 11.04. The source list I found is for 10.04. So how do I install into 11.04? Thanks in advance.
for 32bit ubuntu just download the file following the link below and install
[http://download.ppstream.com/ppstream_1.0.0-1_i386.deb](http://download.ppstream.com/ppstream_1.0.0-1_i386.deb)

for 64bit ubuntu is a little more complicated, I only tested the method below under linuxmint 9 (ubuntu 10.04) and linuxmint 11 (ubuntu 11.04)
1)    sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
2)    sudo apt-add-repository ppa:cnav/ppa
3)    sudo apt-get update
4)    sudo apt-get install ppstream
5) sudo gedit .bashrc
6) add the following line to .bashrc
export LD_LIBRARY_PATH="/lib:/usr/lib:/usr/local/lib:/opt/pps/lib"
7) download the 32 bit version of libphonon4 following the links below.
for 10.04
[http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb)
for 11.04
[http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb)
8) unpack lib files from the deb file and copy it to your /usr/lib32
for 10.04
sudo dpkg -x Downloads/libphonon4_4.6.2-0ubuntu5.2_i386.deb /tmp
sudo cp /tmp/usr/lib/libphonon.so.4.4.0 /usr/lib32/libphonon.so.4

---

### Post by yuzhaoliang on 2011-06-24
> **Khakilang said:**
> Is it possible to install into 11.04. The source list I found is for 10.04. So how do I install into 11.04? Thanks in advance.
for 32bit ubuntu just download the file following the link below and install
[http://download.ppstream.com/ppstream_1.0.0-1_i386.deb](http://download.ppstream.com/ppstream_1.0.0-1_i386.deb)

for 64bit ubuntu is a little more complicated, I only tested the method below under linuxmint 9 (ubuntu 10.04) and linuxmint 11 (ubuntu 11.04)
1)    sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
2)    sudo apt-add-repository ppa:cnav/ppa
3)    sudo apt-get update
4)    sudo apt-get install ppstream
5) sudo gedit /home/your_username/.bashrc
6) add the following line
export LD_LIBRARY_PATH="/lib:/usr/lib:/usr/local/lib:/opt/pps/lib"
7) download the 32 bit version of libphonon4 following the links below.
for 10.04
[http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb)
for 11.04
[http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb)
8) unpack lib files from the deb file and copy it to your /usr/lib32
for 10.04
sudo dpkg -x Downloads/libphonon4_4.6.2-0ubuntu5.2_i386.deb /tmp
sudo cp /tmp/usr/lib/libphonon.so.4.4.0 /usr/lib32/libphonon.so.4
for 11.04
sudo dpkg -x Downloads/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb
sudo cp /tmp/usr/lib/libphonon.so.4.5.0 /usr/lib32/libphonon.so.4
9) logout and login again
10) enjoy your newly installed ppstream

---

### Post by Maheriano on 2011-06-24
And you decided to name it Pee Pee Stream?

---

### Post by Khakilang on 2011-07-03
> **yuzhaoliang said:**
> for 32bit ubuntu just download the file following the link below and install
[http://download.ppstream.com/ppstream_1.0.0-1_i386.deb](http://download.ppstream.com/ppstream_1.0.0-1_i386.deb)

for 64bit ubuntu is a little more complicated, I only tested the method below under linuxmint 9 (ubuntu 10.04) and linuxmint 11 (ubuntu 11.04)
1)    sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
2)    sudo apt-add-repository ppa:cnav/ppa
3)    sudo apt-get update
4)    sudo apt-get install ppstream
5) sudo gedit /home/your_username/.bashrc
6) add the following line
export LD_LIBRARY_PATH="/lib:/usr/lib:/usr/local/lib:/opt/pps/lib"
7) download the 32 bit version of libphonon4 following the links below.
for 10.04
[http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb)
for 11.04
[http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb)
8) unpack lib files from the deb file and copy it to your /usr/lib32
for 10.04
sudo dpkg -x Downloads/libphonon4_4.6.2-0ubuntu5.2_i386.deb /tmp
sudo cp /tmp/usr/lib/libphonon.so.4.4.0 /usr/lib32/libphonon.so.4
for 11.04
sudo dpkg -x Downloads/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb
sudo cp /tmp/usr/lib/libphonon.so.4.5.0 /usr/lib32/libphonon.so.4
9) logout and login again
10) enjoy your newly installed ppstream

I am stuck at no. 6. Which line to add? More help please. I am using 64 bit by the way. Try to make it as simple as possible. Thank you!

[ATTACH]196586[/ATTACH]

---

### Post by Khakilang on 2011-07-19
Somehow after switching to Gnome classic, I realise PPStream was installed and able to use it. But I couldn't see it in Unity .Anyway thanks for you help.

---

### Post by Hilko on 2011-08-23
> **yuzhaoliang said:**
> for 32bit ubuntu just download the file following the link below and install
[http://download.ppstream.com/ppstream_1.0.0-1_i386.deb](http://download.ppstream.com/ppstream_1.0.0-1_i386.deb)

for 64bit ubuntu is a little more complicated, I only tested the method below under linuxmint 9 (ubuntu 10.04) and linuxmint 11 (ubuntu 11.04)
1)    sudo apt-get install libqt4-core libqt4-dbus libqt4-gui libqt4-network libqt4-webkit libqt4-xml libfuse2 mplayer
2)    sudo apt-add-repository ppa:cnav/ppa
3)    sudo apt-get update
4)    sudo apt-get install ppstream
5) sudo gedit /home/your_username/.bashrc
6) add the following line
export LD_LIBRARY_PATH="/lib:/usr/lib:/usr/local/lib:/opt/pps/lib"
7) download the 32 bit version of libphonon4 following the links below.
for 10.04
[http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libphonon4_4.6.2-0ubuntu5.2_i386.deb)
for 11.04
[http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb](http://mirror.pnl.gov/ubuntu//pool/main/p/phonon/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb)
8) unpack lib files from the deb file and copy it to your /usr/lib32
for 10.04
sudo dpkg -x Downloads/libphonon4_4.6.2-0ubuntu5.2_i386.deb /tmp
sudo cp /tmp/usr/lib/libphonon.so.4.4.0 /usr/lib32/libphonon.so.4
for 11.04
sudo dpkg -x Downloads/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb
sudo cp /tmp/usr/lib/libphonon.so.4.5.0 /usr/lib32/libphonon.so.4
9) logout and login again
10) enjoy your newly installed ppstream


Thanks for these instructions. I had to edit step 9) for 11.04 where I added /tmp at the end of
```
sudo dpkg -x Downloads/libphonon4_4.7.0really4.5.0-0ubuntu3_i386.deb

```
just like in the instruction for 10.04.
However, if anyone plans to follow these instructions I recommend using another directory than /tmp. After I logged out I could not login again. I got some weird errors about something that was not correctly configured and exit with error level 2. I was able to fix it by pressing Ctrl+Alt+F1 at the login screen. Then after logging in on the command line I did
```
sudo apt-get clean
sudo chmod 0777 /tmp
``` I rebooted and then I was able to login again.

Then I logged in Ubuntu Classic. There you can find PPS under applications-> Internet. Or you can run it from the command line with the command
```
PPStream
```

Now I can actually watch PPS in Ubuntu, however the sound does not work. Anyway, I am already quite impressed with this result so far. Yuzhaoliang thank you very much for these instructions !

If anyone has the problem with no sound and knows how to fix it please post it here.

---

### Post by yuzhaoliang on 2011-09-20
Thanks Hilko for the correction.

For the no sound problem, try to install ubuntu-restricted-extras.  if still no sound you might need to change the setting under ppstream from oss to alsa for sound out put

---

### Post by Sava on 2011-09-21
yuzhaoliang:

hi bud, could you point me to where can I change the interfact's language to English? I don't speak Chinese hence completely "deaf" to these menu :)

thank you,

---

### Post by yuzhaoliang on 2011-09-30
Sorry bud, you are out of luck, as i know the only version avalible for ppstream is chinese.

---

### Post by singsong on 2012-01-28
> **cnzhuxi said:**
> [IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]i have good expierence the PPStream plugin for totem to wacth online TV or movie,so share with you and the installation as following

1,open terminal and copy code to add source list
                                                            2,then edit and add source list
3,then update the suorce list and install totem-pps on terminal
                         4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list

to see the pic ,find this page
[http://tu.6.cn/pic/show-new/id/5432457/](http://tu.6.cn/pic/show-new/id/5432457/)
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]
Hi ,

I tried this several times , ppstream still not working , can see titles of the movies , click , nothing happens ,wait long time also nothing happen . please help.

---

### Post by singsong on 2012-01-28
> **singsong said:**
> Hi ,

I tried this several times , ppstream still not working , can see titles of the movies , click , nothing happens ,wait long time also nothing happen . please help.
Sorry , my mistake .
Nothing works , cannot get titles or anything .
help.

---

### Post by singsong on 2012-01-28
> **cnzhuxi said:**
> [IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]i have good expierence the PPStream plugin for totem to wacth online TV or movie,so share with you and the installation as following

1,open terminal and copy code to add source list
                                                            2,then edit and add source list
3,then update the suorce list and install totem-pps on terminal
                         4,open the totem, edit/plugin ,select the PPstream,we can see the list on totem list

to see the pic ,find this page
[http://tu.6.cn/pic/show-new/id/5432457/](http://tu.6.cn/pic/show-new/id/5432457/)
[IMG]http://tu.6.cn/pic/show-new/id/5432457/[/IMG]
Hi , I tried this install many times , not successful.
End result , ppstream can see titles ,can expand categories to see titles , click titles , nothing happens , nothing is moving . Help

---

