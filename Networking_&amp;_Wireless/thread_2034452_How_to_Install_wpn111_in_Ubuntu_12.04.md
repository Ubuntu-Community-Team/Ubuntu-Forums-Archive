---
title: "How to Install wpn111 in Ubuntu 12.04"
date: 2012-07-28
forum: Networking &amp; Wireless
---

### Post by aimwin on 2012-07-28
Instructions only is at [https://help.ubuntu.com/community/WifiDocs/Device/wpn111](https://help.ubuntu.com/community/WifiDocs/Device/wpn111)

**[SIZE="4"]Using GUI - NO COMMAND LINE - NO TERMINAL.[/SIZE]**
[COLOR="Blue"][SIZE="2"]**almost but not the same **[/SIZE][/COLOR]as the old [GUI tutorial for 8.04, 9.04, 10.04]("http://ubuntuforums.org/showthread.php?t=844856")

Pre Condition.
A. you must have unzip wpn111 drivers on to Desktop or what ever you like.
B. Fresh Install Ubuntu 12.04
[COLOR="Blue"][SIZE="3"]C. You ***MUST CONNECT*** to the internet ***DURING THIS SETTING UP***[/SIZE] [/COLOR]
with out Internet Connection you have to use BELOW INSTRUCTIONS 
==> Install wpn111 in Ubuntu 12.04 Using command lines <== 

1. At software serch box (Ubuntu Software Center) key in [COLOR="Red"]***[SIZE="3"]ndis[/SIZE]***[/COLOR]  
2. You will see Windows Wireless Drivers (ndiswrapper) come up.

3. Click on Use software source button. Software Center will enable source repositories.

4. Click on More Button. You will see 2 AddOn options.

5. You [COLOR="Red"]**[SIZE="2"]MUST check both ADD ON ..Source for the ndiswrapper....[/SIZE]**[/COLOR]
   [COLOR="Blue"]**[SIZE="3"](fail to do this No.5 will result in unsuccessful installation of wpn111.)[/SIZE]**[/COLOR]

6. Click Install. ==> soon Ndiswrapper icon will be create on Unity Launcher.

7. Click on Ndiswrapper Icon on the Unity Launcher.
   (if no Ndiswrapper icon, then you have to click on "Dash Home" => the left top corner with Ubuntu icon 
    => and type ndis to see ndiswrapper icon)

8.  Key in your password when pop up menu came up.

9.  Click Install New Driver.

10. In the Location box [COLOR="Blue"]**click on the folder icon to browse**[/COLOR] for wpn111 windows driver files, [COLOR="Blue"]**netwpn11,inf**[/COLOR] 

11. Click Install.

12  At the end of installation, ReBoot your computer.

13 Once login, insert the usb wpn111 within 20 seconds the blue LED will start blinking.

14 start configur the wireless security.

=============================================================
I will leave the Command Line Installation, in case the GUI is not working as How to above.

I found out the NO.5 (Check both AddON) fix after I wrote below how to.

**_I had ignore the ADD ON all along, did not realise they are the preliquisite for wpn111,_** and possibly for many other hardware out there.
I don't know why they were not include in the standard installation.
=============================================================

**[SIZE="4"] Install wpn111 in Ubuntu 12.04 Using command lines [/SIZE]**

Two files Attached with this how to at the end of the post.

1. wpn111 drivers.
   or download from [http://downloadcenter.netgear.com/en/product/WPN111](http://downloadcenter.netgear.com/en/product/WPN111)

2. lastest ndiswrapper , include details Installation Manual,
   you can pick the lastest 1.58rc1 or 1.57 stable 
   from 
   [http://sourceforge.net/projects/ndiswrapper/files/](http://sourceforge.net/projects/ndiswrapper/files/)

====> If you are in a hurry to install wpn111 skip to [SIZE="3"]** How To **[/SIZE]section below, and for Newbies,if you don't know how to use Terminal please see section How To use Terminal Section before the How To section.

=================================================================================================
[B][COLOR="Blue"]This section is not valid any longer since I found the fix which enable to do GUI above How To.
I left it here for reference only [/COLOR][/B]
[COLOR="DimGray"][I]=========> Back ground of the installation process is below this line.
I found that my tutorial for wpn111 by GUI ways for 8.04 9.04 and 10.04
([http://ubuntuforums.org/showthread.php?t=844856](http://ubuntuforums.org/showthread.php?t=844856)
[COLOR="Blue"]did not work with 12.04[/COLOR]
[B]
Some how ndiswrapper 1.57 that is installed from either Ubuntu Software Center or Synaptic will not work with wpn111.[/B]

[I][U]But the ndiswrapper 1.57 the same version download from the Ndiswrapper Site and installed manually by command line below, work fine.
[/U][/I]
I wonder if ndiswrapper installed by GUI in Ubuntu 12.04 is working for all for other usb wireless dongle or not. Please help report here.
If it has problems a lot, then it will be another bug in 12.04.[/I][/COLOR]
========================================================================================

=========> ***_To Ubuntu Newbies_*** ==>
So I search for easy new how to, unfortunately it has to be command line.
If you are Newbies and don't know how to use Terminal,

It is the time you start using it now. I use to hate this TERMINAL when I was a newby to Ubuntu too. YOU WILL FIND IT IS VERY POWERFUL TOOL, 
and become a must to uterlise UBUNTU.

For full tutorial how to use Terminal go to [The Terminal is Your Friend!]("https://help.ubuntu.com/community")

============== Brief on **[SIZE="3"]How To use Terminal[/SIZE]** ======
Unity Ubunt 12.04 

Click on Dash home (top left coner ubuntu icon) and type "te" in to the search box, you will see icon "black rectangular box" call Terminal.

Click on it.
Pop up windown will have a prompt waiting

something similar to below sample
[COLOR="Blue"]tbuntu@tbuntu12041:~$[/COLOR] 

for you to [COLOR="Red"]copy[/COLOR] the commands below and [COLOR="Red"]paste[/COLOR] them one line at the time 
([COLOR="SeaGreen"]use mouse to do that, you cannot use Ctrl C and V in the Terminal[/COLOR])
and [COLOR="Red"]press enter[/COLOR] to execute the command.

========> **[SIZE="4"]_HOW TO_[/SIZE]** begin ====>
I use Hp dv1000 (dv1729tu) and

[COLOR="Red"]Pre conditions[/COLOR] that I had

1. [COLOR="Green"]"Fresh installed"[/COLOR] Ubuntu 12.04 and/or 12.04.1 from [http://cdimage.ubuntu.com/precise/daily-live/current/](http://cdimage.ubuntu.com/precise/daily-live/current/)

2. Use [COLOR="Green"]Desktop as working folder[/COLOR].

3. Win wpn111 drivers, all 3 files, are kept in "[COLOR="Green"]/Desktop/win-drivers[/COLOR]"

4. Download ndiswrapper-1.58rc1.tar.gz (199.5 kB)[COLOR="Red"] to "Desktop"[/COLOR]

5. Access Point security is [COLOR="Green"]WEP128bit[/COLOR]

I have not tried others security set up, 
wpn111 used to have issues in using WPA in the old days with old Ubuntu versions.
================================================

[COLOR="Green"]This ***MODIFIED instruction sets*** are from Install manual[/COLOR] in the download file- ndiswrapper-1.58rc1.tar.gz

Start your Terminal

1. [COLOR="Blue"]cd Desktop[/COLOR] 

2. [COLOR="Blue"]tar zxvf ndiswrapper-1.58rc1.tar.gz[/COLOR]

3. [COLOR="Blue"]cd ndiswrapper-1.58rc1[/COLOR]
4. [COLOR="Blue"]make unistall[/COLOR]
5. [COLOR="Blue"]make[/COLOR]
6. [COLOR="Blue"]sudo make install[/COLOR]
7. [COLOR="Blue"]cd ..[/COLOR]
8. [COLOR="Blue"]cd win-drivers[/COLOR]
9. [COLOR="Blue"]ndiswrapper -i netwpn11.inf[/COLOR]
===========> plug in the wpn111 now.
10. [COLOR="Blue"]modprobe ndiswrapper[/COLOR]

Wait 5-15 seconds the blue LED should start blinking.

If it is not blinking after 20+seconds, 
[COLOR="Red"]REBOOT your computer[/COLOR] and when it is login,
plug in your wpn111, and try No. 10 again.

11. start config the wireless lan, by clicking on wireless applet
top right hand side next to speaker icon, and connect.
key in password.

---

### Post by avneetsb on 2012-10-13
Thanks for the info. It working for me. But many times after reboot it doesn't work. I have to unplug my USB wifi dongle and put it back to make it work. Is there any way to fix this?

-Avneet

---

