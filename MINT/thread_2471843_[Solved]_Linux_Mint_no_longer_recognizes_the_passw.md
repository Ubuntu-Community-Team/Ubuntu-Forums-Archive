---
title: "[Solved] Linux Mint no longer recognizes the password"
date: 2022-02-10
forum: MINT
---

### Post by martin357 on 2022-02-10
Hi All,

I'm on Linux Mint. I wanted to access my PC as usual, but when I enter the password, the system does not take it into account. I can't access the desktop!

It goes back and re-displays the same access page to enter the password again!

The password I enter is correct, I did not forget it. Because, when I enter a wrong password, the error message appears "Invalid Password, Please Try again".

It's like the system is stuck. Although it recognizes the password, but it does not enter.

I am absolutely blocked, and I cannot access the desktop.

Also, When I click <ctrl><alt><F1> the terminal doesn't appear! All I get is a screen that freezes and the mouse pointer disappears.

I removed the hard drive and had it explored in a Linux Live DVD. None of my files are found! The "Home/user" file is completely empty!

How can I get access again?

Or else, how to remove the password completely?

Your help is highly appreciated. I want to recover my work files that are on the disk.

Thank you,

---

### Post by guiverc on 2022-02-10
Linux Mint is not an [*official flavor* of Ubuntu]("https://ubuntu.com/download/flavours") so you've posted in the wrong section of this site.

For a user to successfully login to a GUI session, there must be sufficient space in $HOME or the user account (`/home/$USER`), so work files can be created as are needed by a GUI, if they cannot be written (ie. no space or no access to $HOME), the GUI login will fail and user is returned to the greeter (DM). No error message occurs (*as you successfully passed the DM/greeters login; but the subsequent GUI starting up failed causing you to return to the greeter, thus the greeter sees it as a logout as GUI session ended*).

A lack of space issue should **not** impact a text login, thus using Ctrl+Alt+F4 should start a text terminal allowing login.  You didn't provide release details, where Ctrl+Alt+F1 does not represent a text terminal for many Ubuntu releases (eg.* Ctrl+Alt+F1 is where I access my GUI on my Ubuntu system having been so for some time; alas you didn't provide release details so adjust for your unstated release*)[B][I].

[/I][/B]I'd explore your issues from a *live* system, ie. checking your file-system table (`/etc/fstab`; but ensure you're checking the installed system on disk & not the *live* systems entry). I'd check the file-systems for errors (*I would also check drive health & other hardware issues; its unrelated but I do it whenever something unexpected occurs*); and try booting with messages showing so you can look for any errors or problems occurring etc.  If you made any changes to that system during the last working session, or any other installed OS one the box since then, I'd explore that too.

Linux Mint differs to Ubuntu and *flavors* in that it also has an extra layer of software (runtime *adjustments* because Mint *devs* cannot upload to Ubuntu repositories but rely on them, thus using the *hack* to achieve their goal...) but I don't keep up with packages they use/require *adjustments* to so I've ignored that extra detail that is Linux Mint specific.

---

### Post by QIII on 2022-02-10
Moved to ***MINT***

---

### Post by martin357 on 2022-02-13
Thank you, @guiverc, for your reply,

I have been trying for the last few days to find a solution to regain access to my PC, but so far I can't access it.

I launched the SSD on Live DVD (as an external drive under Windows, because Live DVD does not boot while the Linux SSD was inserted as an internal drive!), I gathered this information (see screenshots):

1/ The disk is full: So, what files can I delete to free up space?
It shows that it is full when in reality it is only a little over 50% full. Maybe a virus has written files on the hard disk and filled it up! Is this possible under Linux? I had not installed an antivirus, because I had read that it was not necessary under Linux.

2/ I don't see my files and folders in the "Home/user" directory! Is Home empty, and how could these files disappear?
Are the "Home" directory and its contents preserved?

3/ The ".ICEauthority" and ".Xauthority" files are not found!

4/ Is the size of "Swapfile" normal?

5/ When I first installed the program, I remember setting up the "Timeshift" backup using the "ext" partition on an external hard drive. 
How can I restore the system when I'm locked out?

6/ I can't enter the password after typing "Ctrl+Alt+F2". I get a message saying "Login is incorrect"!

7/ I provide here the content of the "fstab" file.

How can I solve this problem and connect to the desktop again?

Thank you all,


Please, found the screenshots here:
[https://www.screencast.com/t/1EORPStRZph](https://www.screencast.com/t/1EORPStRZph)


My Distro:
Linux Mint 20 Ulyana / Desktop: Cinnamon 4.6.7 / Kernel:  5.4.0-54-generic x86_64 / bits: 64 / CPU: Intel Core i3-4010U 1.7Ghz /  RAM: 8Go

---

### Post by guiverc on 2022-02-13
I can't know what size your swapfile is; i see only the entry for it in your file-system table which reveals nothing about the size; you'll need to look at /swapfile to see what filesize you've allocated to it.

I can't see what files you have installed on your system, so can't offer advice there. Yes Linux Mint contains extra *attack vectors* that Ubuntu does not have, making it easier for virus/malware to attack a Linux Mint system when contrasted with either Debian or Ubuntu, **however** that *additional* risk with Linux Mint because of their use of *runtime adjustments* is not large; and mostly it's the reduced security decisions they make so Ubuntu *security fixes* do not negatively impact Linux Mint systems because of their use of *runtime adjustments*, and you've provided no details as to your settings (*Linux Mint used to suggest lower settings than they have in more recent releases in attempts to improve security*) so I cannot comment there where it matters most. Linux Mint have been raising their security profile decisions; so to an extent it may boil down to how closely you read their release notes and if you followed their advice (ie. re-install and not *release-upgrade* is common for Linux Mint as is required to raise security profiles).

Anti-virus is usually used to protect windows systems when the GNU/Linux host is file-sharing and thus serving files to windows machines. Yes other forms of malware impact any OS (eg. *web browsers can be attached the same regardless of OS*) but virus by definition was a form of malware that specifically relied on windows to propagate/infect.

If you're switching to a text terminal (Ctrl+Alt+F2) then I would expect a text terminal to allow login, not reject due to invalid password; that to me is a red flag, but I've not had a Linux Mint install since maybe 2017 so I'm not well suited to any differences they've made (*this install is over a Linux Mint system that I used to test this box before I installed Ubuntu I'm now so I could (a) have a look at Linux Mint, but also (b) ensure this hardware was trustworthy*).

Disk space problems vary; the most common issue I see is people not allocating enough space for what they intend to do with their systems, where the best fix in my opinion is to increase partition size. Ubuntu Desktop has since 2017 (*prior to 17.10 or the 2017-October release*) recommended a minimum size of 25GB because most users add applications to their installed systems, don't always apply upgrades daily (*upgrades need space** to download then install etc*) & other reasons; yet many bloggers still write you can use 8 or 10GB (*yes you can if you're installing it just to test, record a vlog/blog & not live with longer term* *because you'll start again with the next distro being reviewed*). You've provided no details though about your disk allocation, what applications (*& package types used to install them with*), what is important to you (ie. *what can be deleted, what cannot*), so I can't really advise sorry.

---

### Post by martin357 on 2022-02-15
It's solved. 

For all users who encounter this kind of problem, the solution is to temporarily set the percentage reserved for the root of the file system to "0" to allow the connection, with this command:
sudo tune2fs -m0 /dev/sda2  

Once the connection is successful, and the cleanup is done, we can return to the standard percentage of "5": 
sudo tune2fs -m5 /dev/sda2

(replace "sda2" with your partition name)


Thanks All,

---

