---
title: "Latest Nvidia Driver Help"
date: 2008-06-12
forum: Multimedia Software
---

### Post by popocus on 2008-06-12
I have been trying to install  the latest driver for my NVIDIA 9600 GT manually in Hardy Heron but when i use the command:

/etc/init.d/gdm stop

it puts into command line where it stays in running boot script (etc/rc.local)

i cannot do anything i type and nothing happens 

if any one out there can help it will be greatly appreciated 
thank you.

---

### Post by blazercist on 2008-06-12
do not issue this command from the gui, you need to ctrl+alt+f1 before you issue sudo /etc/init.d/gdm stop

ctrl+alt+f1 will drop you to a command line and from there you can run this command and execute the driver binary

---

### Post by popocus on 2008-06-12
Thanks but now the problem is that for every command it ask for pass ok but everytime i type it in it says wrong login pass.

---

### Post by Pjotr123 on 2008-06-12
Better try Envy first:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

---

### Post by Milardo on 2008-06-12
you have to set a root password in gui first because you need to be root when installing driver. In gui type in termianl sudo passwd root. By the way I tried to install it but after finishing I got nothing on my screen. Best I think to install the driver from add/remove programs type nvidia in search box.

---

### Post by blazercist on 2008-06-12
@milardo: the nvidia driver in the repos doesn't support the 9600 GT, he needs the new 171.06 or higher proprietary driver from nvidia.  

@OP: you need to set a password for your account before you can change things like drivers or administrative settings.  once you do that you can follow the instructions you have for installing the driver.

1. ctrl+alt+f1
2. sudo /etc/init.d/gdm stop
3. sudo chmod +x NVI*
4. sudo ./NV*
5. Follow onscreen instructions, I recommend not merging xorg file and just allowing the driver installer to overwrite your existing one, make sure to back it up first.

---

### Post by blazercist on 2008-06-12
and another thing, I would not recommend using envy, it tends to muck things up, and why would you want to install a peice of software in order to install another peice of software?  besides i think this method is easier anyway.

I'm really unclear on this because I'm relatively new to *nix also but is it possible for someone to make a .deb from the new drivers?  I kno the newer ATI drivers allow for creating .deb packages based on distro do the NVIDIA drivers support that?

---

### Post by popocus on 2008-06-12
i try to do your method Blazer but i still cannot get past the login incorrect even after i set root pass

---

### Post by Pjotr123 on 2008-06-12
> **blazercist said:**
> and another thing, I would not recommend using envy, it tends to muck things up, and why would you want to install a peice of software in order to install another peice of software?  besides i think this method is easier anyway.

I'm really unclear on this because I'm relatively new to *nix also but is it possible for someone to make a .deb from the new drivers?  I kno the newer ATI drivers allow for creating .deb packages based on distro do the NVIDIA drivers support that?

Envy used to be bad, but it has improved and is now even in the official repositories of Ubuntu! 

Envy is safe nowadays. It's the easiest way to install the (almost) latest driver from Nvidia and ATI, when the restricted driver in the Ubuntu repo's is too old for your card.

---

### Post by SteveNorman on 2008-06-12
Are you the only user on the computer? your sudo password should be the same as your loggin password.


a thorough guide on the new nvidia driver install by starcannon

```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```

---

### Post by blazercist on 2008-06-12
@popocus: I think that its a mistake on my part, root is disabled by default under ubuntu if im not mistaken... what you need to do is set the password for your user account, it should've asked u during installation to set a password, but in any case it should be:

sudo passwd "your_username_here"  without the "" marks obviously

@Pjotr123:  Sorry, I didn't mean to insinuate that envy is bad or anything like that, I'm just saying that I haven't had any good experiences with it although I only used it once a long time ago, Its just my opinion that doing it the way I stated is simplest for me.


SteveNorman's guide is very thorough and looks like it covers all the angles so I endorse it... it just doesn't address popocus' issue with the password which is unrelated to the driver installation really.

---

### Post by pravin03 on 2008-08-02
1. ctrl+alt+f1
2. sudo /etc/init.d/gdm stop
3. sudo chmod +x NVI*
4. sudo ./NV*
5. Follow onscreen instructions, I recommend not merging xorg file and just allowing the driver installer to overwrite your existing one, make sure to back it up first.


I installed like this. Driver not working.I want to uninstall it now and use driver from repo.
How can I uninstall and cancel the reconfiguration of X?

---

