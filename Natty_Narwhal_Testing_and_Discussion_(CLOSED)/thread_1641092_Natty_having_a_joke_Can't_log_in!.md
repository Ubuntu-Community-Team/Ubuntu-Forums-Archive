---
title: "Natty having a joke? Can't log in!"
date: 2010-12-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-12-08
I just ran a couple of minor updates and the Start button turned red for a reboot. So I rebooted and I am now greeted by the default purpleish screen with a log in dialogue box. It's not set up to do this but what the hell! My username is there by default and I click on it and then enter my password. The screen goes black and there is a flash of a message in the top left corner which I can't read (too fast) and the log in screen comes back. Again and again and again.
The caps lock isn't on, the number lock isn't on but it won't let me get past the log in screen.
I'm stumped :(
Suggestions on a postcard please :-)

---

### Post by ronacc on 2010-12-08
I'm sorry , the OS you have reached is not in service at this time .:lolflag:

---

### Post by douham on 2010-12-08
Same thing has just happened to me. Login screen shows; selecting user and typing password as noraml, Natty begins to login as normal but reverts back to the login screen. Occurs no matter which desktop session I try.

---

### Post by Quackers on 2010-12-08
> **ronacc said:**
> I'm sorry , the OS you have reached is not in service at this time .:lolflag:

That's the one!

Let me in! It's cold out here!

---

### Post by siriusguy on 2010-12-08
Same here.   Have tried booting single-user and updating and still doesn't work.

---

### Post by coffeecat on 2010-12-08
I'm not going to be of much help, but I upgraded last (without problem) about 4 hours ago. I've just done another apt-get update and apt-get upgrade to see what was on offer, and I can only assume the offending package is among this little lot:

```
The following packages will be upgraded:
  dbus dbus-x11 gnome-mag gnome-session-canberra gnome-utils-common
  indicator-application libappindicator0.1-cil libappindicator1
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libdbus-1-3
  libgnome-mag2 libimobiledevice1 libtelepathy-farsight0 libtelepathy-glib0
  python-appindicator software-center
```Needless to say:

```
Do you want to continue [Y/n]? n
Abort.
```The only suggestion I have is to go to tty1 and see if you can login. At least you can see whether this is a password issue.

---

### Post by ronacc on 2010-12-08
how did you update ? I went to do my evening update a while ago via synaptic and it wanted to remove some stuff I didn't like the looks of so I decided to wait .

---

### Post by coffeecat on 2010-12-08
> **ronacc said:**
> it wanted to remove some stuff I didn't like the looks of so I decided to wait .

Yup. [We're in for a rough ride.]("http://ubuntuforums.org/showthread.php?t=1640839")

---

### Post by cariboo on 2010-12-08
I can get to desktop, by starting in recovery mode and selecting resume from the menu. I then login and type:

```
startx
```

at the prompt.

---

### Post by Quackers on 2010-12-08
> **ronacc said:**
> how did you update ? I went to do my evening update a while ago via synaptic and it wanted to remove some stuff I didn't like the looks of so I decided to wait .

Via Synaptic, but the updates that frighten you I have run already without incident! The nvidia-current and nvidia-settings and ubuntu-desktop were no problem! I even rebooted - rather bravely I think! :-) It's the tiny ones I've just run. I think one was d-bus something or other and 2 others iirc.

How do I get to tty1?

---

### Post by douham on 2010-12-08
> **coffeecat said:**
> I'm not going to be of much help, but I upgraded last (without problem) about 4 hours ago. I've just done another apt-get update and apt-get upgrade to see what was on offer, and I can only assume the offending package is among this little lot:

```
The following packages will be upgraded:
  dbus dbus-x11 gnome-mag gnome-session-canberra gnome-utils-common
  indicator-application libappindicator0.1-cil libappindicator1
  libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libdbus-1-3
  libgnome-mag2 libimobiledevice1 libtelepathy-farsight0 libtelepathy-glib0
  python-appindicator software-center
```Needless to say:

```
Do you want to continue [Y/n]? n
Abort.
```The only suggestion I have is to go to tty1 and see if you can login. At least you can see whether this is a password issue.

Have tried tty1, 2 etc. I can login ok, but the the login prompt is at the bottom of the screen and the text is not scrolling up the screen as I type, and soon loose where my cusor is. Reverting to tty7 takes me back to back to the gdm login screen which indicates that my user is already logged in.

---

### Post by ronacc on 2010-12-08
ctrl>alt>F1    or F2 > F6 for those tty's

---

### Post by Quackers on 2010-12-08
Recovery mode does exactly the same thing - loops to log in screen.
Will try ctrl + alt + F1 but I suspect that a fix may be needed from chrooting in? Back in 5

---

### Post by cariboo on 2010-12-08
I dropped to a netroot, then typed exit, and selected resume, it took me to a login prompt, and from there I typed startx, after logging in.

If you can get to a console stop gdm:

```
sudo service gdm stop
```

and then type startx.

---

### Post by Quackers on 2010-12-08
> **cariboo907 said:**
> I dropped to a netroot, then typed exit, and selected resume, it took me to a login prompt, and from there I typed startx, after logging in.

If you can get to a console stop gdm:

```
sudo service gdm stop
```

and then type startx.

Thanks I'll try that cariboo907.

I tried ctrl alt F1 and it allowed me to log in but on entering startx it said
Xauthority file home/myuser/,xauthority does not exist
Fatal server error
Server is already active for display 0

Back soon :-)

ctrl alt F7 just stops at checking battery state.

---

### Post by Quackers on 2010-12-08
Ok.
I did ctrl alt F1 from the log in screen.
Logged in and then typed ```
sudo service gdm stop
```
when gdm stopped I typed ```
startx
```
and the desktop started up. Loads of panel applet failures to load, but they all reloaded after clicking on the reload buttons.
No Unity though at the moment.

Thanks cariboo907. :-)

Awaiting further developments :-)

---

### Post by Quackers on 2010-12-08
Unity is back :-)
I just ticked the Unity plugin box again in ccsm. I now have a bottom panel that I didn't have before but that's ok.
I'm not rebooting for at least a week :-)

---

### Post by coffeecat on 2010-12-08
> **Quackers said:**
> I'm not rebooting for at least a week :-)

What I'm going to do in a moment is to defer those latest updates, shut the thing down, go to bed, and then see what the other hemisphere has made of all this when I get up in the morning. :p

Thanks for the warning, Quackers! :)

---

### Post by douham on 2010-12-08
Nofair. I live in the other hemisphere. It's nearly 8am where I live.

---

### Post by ronacc on 2010-12-08
I see there hasn't been a new daily-live for 2 days so it looks like the cd's are giving problems too .

---

### Post by Quackers on 2010-12-08
> **coffeecat said:**
> What I'm going to do in a moment is to defer those latest updates, shut the thing down, go to bed, and then see what the other hemisphere has made of all this when I get up in the morning. :p

Thanks for the warning, Quackers! :)

Are you a cat or a chicken? ;):D:D

---

### Post by cariboo on 2010-12-08
I put up a sticky warning about update problems for the next couple of days.

It's only 4:00PM here, I've still got a full 8 hours to screw things up. :)

---

### Post by Quackers on 2010-12-08
It's midnight here. I'm still trying :-)

BTW you're welcome coffeecat :-)

---

### Post by douham on 2010-12-08
None of my tty's are working. The login prompt is about 1 line from the bottom of the screen. I can type my user name, then <enter>, but the text is no longer scrolling up the screen. It is impossible to see if any commands are working.


edit: booting in recovery mode enables me to get in via console.

---

### Post by Quackers on 2010-12-08
> **douham said:**
> None of my tty's are working. The login prompt is about 1 line from the bottom of the screen. I can type my user name, then <enter>, but the text is no longer scrolling up the screen. It is impossible to see if any commands are working.


edit: booting in recovery mode enables me to get in via console.
Nice one :-)
I didn't have that problem.
I plan on doing no updates for at least a couple of days and definitely no reboots till then :-)

---

### Post by jaco223 on 2010-12-08
having the same prob here. i'm going to wait to do any updating, i reinstalled twice. painful. i googled the prob and found something old, but it seems reasonable, maybe a guru can give better advice on this. here is what i found.

sudo apt-get install --reinstall gdm && sudo dpkg -reconfigure gdm

haven't tried it though .....

any thoughts?

thanks,

jaco

---

### Post by Quackers on 2010-12-08
Have you tried what I posted in post #16?

---

### Post by autocrosser on 2010-12-08
Hmmm--I got the problem also---got to the login screen & changed TTY--logged in & did a "sudo stop gdm", then "startx" & went back to the main TTY--Long story short---I'm in and waiting for more updates:D:D

Crud---that breakage was no fun----lasted too short:p:p

---

### Post by Quackers on 2010-12-08
Lol, me too, but not going to use any for a couple of days :-) I've got 4 already that won't install! I wasn't going to install them anyway - just wanted to see if they would :-)

---

### Post by autocrosser on 2010-12-08
> **jaco223 said:**
> having the same prob here. i'm going to wait to do any updating, i reinstalled twice. painful. i googled the prob and found something old, but it seems reasonable, maybe a guru can give better advice on this. here is what i found.

sudo apt-get install --reinstall gdm && sudo dpkg -reconfigure gdm

haven't tried it though .....

any thoughts?

thanks,

jaco

Jaco---I don't think that would do much good---the problem is Python--I reinstalled GDM for grins & the output tells the tale:```
dean@linux:~/Desktop$ sudo aptitude reinstall gdm
[sudo] password for dean: 
The following packages will be REINSTALLED:
  gdm 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 17 not upgraded.
Need to get 0 B/763 kB of archives. After unpacking 0 B will be used.
Preconfiguring packages ...              
(Reading database ... 350767 files and directories currently installed.)
Preparing to replace gdm 2.32.0-0ubuntu1 (using .../gdm_2.32.0-0ubuntu1_amd64.deb) ...
Unpacking replacement gdm ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for gconf2 ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Setting up gdm (2.32.0-0ubuntu1) ...

```

Notice all the Python support in GDM---wait till the rest of the apps are rebuilt for Python 2.7......

---

### Post by Quackers on 2010-12-08
Oh no! I'm going to need to reboot sooner than I'd hoped :-( That damned memory leak in nm-applet is swallowing ram. Half used already :-(

---

### Post by autocrosser on 2010-12-08
Ah--the joys of Alpha testing:D

Just look at it this way--you get extra time brushing up on your terminal skills:p

---

### Post by Quackers on 2010-12-08
There's always a silver lining to any cloud :-)
At least I know how to get back in now :-)
Time for bed now! Night all

---

### Post by autocrosser on 2010-12-08
Repeat after me:

BRING ON THE BREAKAGE!!!!!!:guitar:

(of course it helps having 2 backup installs to fall back on--always be prepared when you Alpha test)

---

### Post by ronacc on 2010-12-08
checking the nm memory leak bug I see that the importance has been bumped up to high , still unassigned but atleast some movement .

---

### Post by ronacc on 2010-12-08
> **autocrosser said:**
> Ah--the joys of Alpha testing:D

Just look at it this way--you get extra time brushing up on your terminal skills:p

and also you language skills (as in how many can you curse in ) :P

---

### Post by autocrosser on 2010-12-08
LOL!!!!!  Let's see--English--some Spanish---some Norwegian & a touch of French---will that do????

:popcorn:;);)

---

### Post by ronacc on 2010-12-08
should suffice if the breakage isn't too bad .;)

---

### Post by Starks on 2010-12-08
Killing the gdm service did the trick.

---

### Post by kyleabaker on 2010-12-08
> **autocrosser said:**
> Ah--the joys of Alpha testing:D

Just look at it this way--you get extra time brushing up on your terminal skills:p

Ace. :D

...but as much as I love clicking that update button, I think I'll wait this one out. :popcorn:

---

### Post by autocrosser on 2010-12-09
> **kyleabaker said:**
> Ace. :D

...but as much as I love clicking that update button, I think I'll wait this one out. :popcorn:

AWWWW--come on in--the water is fine:D

---

### Post by ComputerJy on 2010-12-09
So did anyone actually report this bug??

---

### Post by chrismine on 2010-12-09
> **cariboo907 said:**
> I can get to desktop, by starting in recovery mode and selecting resume from the menu. I then login and type:

```
startx
```

at the prompt.

Doesn't work for me - I login with username and password - it gives a message - rmdir and something about byobu cannot be removed.
The message is: rmdir: failed to remove 'home/chrisjan/.byobu' Directory not empty

To stop gdm has the same result as hereunder:

When I type startx it goes to the login screen where I login again - the screen goes black and return to the login screen.

If I type startx from root prompt I am able to login to a root account.

---

### Post by chrismine on 2010-12-09
> **autocrosser said:**
> Repeat after me:

BRING ON THE BREAKAGE!!!!!!:guitar:

(of course it helps having 2 backup installs to fall back on--always be prepared when you Alpha test)

NOOO you're chicken - I have no backups - doing it naked with no fallbacks!

---

### Post by chrismine on 2010-12-09
> **autocrosser said:**
> Repeat after me:

BRING ON THE BREAKAGE!!!!!!:guitar:

(of course it helps having 2 backup installs to fall back on--always be prepared when you Alpha test)

NOOO you're chicken - I have no backups - doing it naked with no fallbacks!

Except - if you can call Windows vista A FALLBACK!

---

### Post by Quackers on 2010-12-09
At the log in screen press ctrl+alt+F1 then type ```
sudo service gdm stop
``` and hit enter then type startx and hit enter.

---

### Post by Quackers on 2010-12-09
> **ronacc said:**
> checking the nm memory leak bug I see that the importance has been bumped up to high , still unassigned but atleast some movement .

Excellent, thanks.

I can swear in French, German, Hungarian, Polish, Italian, Spanish and English. I should be able to cope :-)

ComputerJy,
we have been warned already. It's not a bug to be reported.

---

### Post by coffeecat on 2010-12-09
Mornin', Quackers!

This all reminds me of when I used  Gentoo. An upgrade of python was always - er fun, but nothing could beat a version upgrade of gnome. You'd start in the morning - 175 packages to be downloaded and compiled and you'd leave the 'emerge -Du world' running. Slowly, bit by bit, the gnome desktop would fall apart in front of your eyes as essential libraries and dependencies were replaced beneath its feet. Then, without fail, halfway through there would be a compile failure or somesuch. The GUI would be unusable and often you had an unresponsive keyboard so that you couldn't sashay into a tty.

A quick recourse to Gentoo forums using another distro to find the workaround (*real* Gentoo users would use a CLI-based text browser - none of this namby-pamby GUI nonsense for them), and off you went again. Eventually, usually late evening, the upgrade would be done and you would have a more-or-less usable gnome desktop from which you could start the task of editing and updating 101-odd config files.

Those were the days. :nostalgic sigh: :|

---

### Post by Quackers on 2010-12-09
Morning CC :-)
That sounds like fun, fun, fun :-)
No thanks.

---

### Post by chrismine on 2010-12-09
[QUOTE=Quackers;10218402]Excellent, thanks.

I can swear in French, German, Hungarian, Polish, Italian, Spanish and English. I should be able to cope :-)

Nothing works for me - look like it is time for me to reinstall - I am speechless!!!!!

---

### Post by Quackers on 2010-12-09
What is happening on your system chrismine?

---

### Post by ronacc on 2010-12-09
> **chrismine said:**
> [QUOTE=Quackers;10218402]Excellent, thanks.

I can swear in French, German, Hungarian, Polish, Italian, Spanish and English. I should be able to cope :-)

Nothing works for me - look like it is time for me to reinstall - I am speechless!!!!!

speechless maybe but theres a gesture for it in Italian :lolflag:

---

### Post by coffeecat on 2010-12-09
> **chrismine said:**
> Nothing works for me - look like it is time for me to reinstall - I am speechless!!!!!

If you reinstall and update, you'll likely end up the same. [See this sticky]("http://ubuntuforums.org/showthread.php?t=1641151").

Perhaps it would be better to wait for a few days, and then do an update from the CLI, either in recovery mode or from a virtual terminal.

---

### Post by rafik24 on 2010-12-09
Hi All,

well as being said this is very early not even alpha testing so love it or just wait for the release.

Enough said, 

for those of you that are unable to get to the tty because the cursor is at the bottom right of the screen:

At bootup in grub menu press the e key for edit and look for 

set gfxpayload=$linux_gfx_mode 

replace by

set gfxpayload=1024x768 (or whatever your screen resolution is)

you can also change this setting in /boot/grub/grub.cfg for a quick fix

once booted you can get to tty by pressing Ctrl+alt+F1

login using your user account

then type service stop gdm

then sudo X &

then type gnome-session 
(this way you can run gnome using your user account as usual)

if there is no window manager running (window borders not decorated) press Ctrl+alt+t to launch the terminal

in the terminal run compiz --replace &

in order to run unity start ccsm and at the bottom check the Ubuntu Unity Plugin checkbox

Hope this helps till we get all packages using python 2.7

all the best,

Rafik

---

### Post by bedbug on 2010-12-09
[COLOR="Red"]Temporary Solution[/COLOR]

echo "deb [http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu](http://ppa.launchpad.net/robert-ancell/lightdm/ubuntu) maverick main" | sudo tee -a /etc/apt/sources.list

sudo apt-get install  lightdm

---

### Post by Harry33 on 2010-12-09
And now there is bug a report on this issue:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/688013](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/688013)

You may go there and check "Yes, this affects me".

---

### Post by jaco223 on 2010-12-09
> **autocrosser said:**
> Jaco---I don't think that would do much good---the problem is Python--I reinstalled GDM for grins & the output tells the tale:```
dean@linux:~/Desktop$ sudo aptitude reinstall gdm
[sudo] password for dean: 
The following packages will be REINSTALLED:
  gdm 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 17 not upgraded.
Need to get 0 B/763 kB of archives. After unpacking 0 B will be used.
Preconfiguring packages ...              
(Reading database ... 350767 files and directories currently installed.)
Preparing to replace gdm 2.32.0-0ubuntu1 (using .../gdm_2.32.0-0ubuntu1_amd64.deb) ...
Unpacking replacement gdm ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for gconf2 ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-support ...
Setting up gdm (2.32.0-0ubuntu1) ...

```Notice all the Python support in GDM---wait till the rest of the apps are rebuilt for Python 2.7......

Auto

Thanks .....I see what you're saying, Guess I ws desperate for a fix LOL!
I'll wait for updates...... :)

Jaco

---

### Post by Starks on 2010-12-09
Grr....

I can't get my sound to work with these workarounds.

---

### Post by Harry33 on 2010-12-09
> **Harry33 said:**
> And now there is bug a report on this issue:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/688013](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/688013)


Well what do you know.
Now this bug report in the quote above has been marked as a duplicate of the bug #654578. Here:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/654578](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/654578)

This thread (which was started by Quackers about 15 hours ago) is about issues with Python2.7 and Gdm.
The other bug#654578 describes same symptoms (repeated login screen loop) but it cannot be caused by the python2.7.

At least this is how I see it.

---

### Post by autocrosser on 2010-12-09
> **chrismine said:**
> NOOO you're chicken - I have no backups - doing it naked with no fallbacks!

Except - if you can call Windows vista A FALLBACK!

Yas--no windozs here--I'm testing both Unity & Gnome-Shell/Gnome3, so 2 Natty installs & I always have a "stable" install as backup--been doing this for 5 years now...Of course, this is my main system--i7 with a Gigabyte board & 2.5TB of drives.......

---

### Post by Harry33 on 2010-12-09
IMPORTANT INFO:

Martin Pitt has narrowed this bug to packages
- libcanberra-gtk-module and
- libcanberra-gtk3-modules

Purge those packages (they are only recommended installations) and you will have a working GDM again.
 See bug #654578
Here:
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/654578](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/654578)

Martin Pitt says purging libcanberra-gtk3-module solves this.
There will be a new update of libcanberra soon.

---

### Post by Harry33 on 2010-12-09
Well that was a fast fix released.
The upgrade is already in Launchpad and it solved this issue:
libcanberra_0.26-1ubuntu2.

---

### Post by Penguin360 on 2010-12-09
> **Harry33 said:**
> IMPORTANT INFO:

Martin Pitt has narrowed this bug to packages
- libcanberra-gtk-module and
- libcanberra-gtk3-modules

Purge those packages (they are only recommended installations) and you will have a working GDM again.
 See bug #654578
Here:
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/654578](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/654578)

Martin Pitt says purging libcanberra-gtk3-module solves this.
There will be a new update of libcanberra soon.

Yes, I had the same problem. Purging libcanberra-gtk3-module fixed the problem. The bug status shows that the bug is fixed in 0.26-1utuntu2 version, but it is not in Synaptic yet.

---

### Post by ronacc on 2010-12-09
thanks for the heads up , purging libcanberra(s) got me back to a crippled desktop but it was crippled before the python updates started , just marking time until the daily's resume and when I get one that boots I'll reinstall .

---

### Post by chrismine on 2010-12-09
> **Quackers said:**
> What is happening on your system chrismine?
Hello Quackers

Thanks for your interest - I managed to get back into my system by purging the libcanberra packages.

---

### Post by Penguin360 on 2010-12-09
I decided to re-install 10.10 and wait until a more stable release of 11.04 is out.

P.S. The size of alpha 1 of 11.04 is too big for a regular CD, it is 717MB, why?

---

### Post by arpanaut on 2010-12-09
> **CodingBeaver said:**
> I decided to re-install 10.10 and wait until a more stable release of 11.04 is out.

P.S. The size of alpha 1 of 11.04 is too big for a regular CD, it is 717MB, why?


From the Common Problems Sticky:

**I downloaded the daily CD image, but it's oversized and I can't burn it on a CD.**

The daily images get built automatically, and due to the rapid and  asynchronous nature of uploads to the development branch, no effort can  be made to make them fit on a CD on a daily basis; such an effort is  only made for the milestones. Note that you can still use oversized CD  images for testing in a virtual machine.

Just didn't happen this Milestone  Why?...  probably time constraints

---

### Post by cariboo on 2010-12-09
> **CodingBeaver said:**
> I decided to re-install 10.10 and wait until a more stable release of 11.04 is out.

P.S. The size of alpha 1 of 11.04 is too big for a regular CD, it is 717MB, why?

Where did any one say an alpha release was supposed to be stable? :) :) I'd suggest you wait until the RC.

---

### Post by Harry33 on 2010-12-09
> **cariboo907 said:**
> Where did any one say an alpha release was supposed to be stable? :) :) I'd suggest you wait until the RC.

This is so true.
People out there tend to believe ubuntu is already a rolling release.
But no, alfa stages will break at some point.
Well, after all, all breakages and fixes also makes our knowledge better.
This is why Linux is so fine.
The more you learn, the more you are able to do.

---

### Post by Penguin360 on 2010-12-09
Understood alpha release is not supposed to be "stable", and I don't mind experiencing unexpected crashes of applications and then spending time on fixing them, but I don't have time and effort to fix login issue. It is frustrating that you suddenly cannot login after a system update.

I don't want to wait until RC, just until alpha 2 or beta is released so I don't have to struggle with login.

---

### Post by plun on 2010-12-09
> **CodingBeaver said:**
> Understood alpha release is not supposed to be "stable", and I can stand unexpected crashes of applications, but I don't have time and effort to fix login issue. It is frustrating that you suddenly cannot login after a system update.

I don't want to wait until RC, just until alpha 2 or beta is released.

Why don't you just start in recovery ??

Login

```
startx
```

Update your packages.... fixed packages are at least available from main...probably from mostly all of the mirrors !

---

### Post by coffeecat on 2010-12-09
> **CodingBeaver said:**
> Understood alpha release is not supposed to be "stable", and I don't mind experiencing unexpected crashes of applications and then spending time on fixing them, but I don't have time and effort to fix login issue. It is frustrating that you suddenly cannot login after a system update.

I don't want to wait until RC, just until alpha 2 or beta is released so I don't have to struggle with login.

@CodingBeaver, I have to say that I find this an extraordinary statement. The whole point of alpha and beta testing is to find bugs, discuss them here and report them on Launchpad so that the devs can fix them. Bugs will include things such as failure to login to the GUI - or even worse. I remember a couple of releases ago when python (*again* :rolleyes:) broke badly and many apps, including update manager, wouldn't run at all. That was - er - fun!

If you are running an alpha or beta and not experiencing serious breakages then something is very wrong. It's also very boring.

Enjoy the rough ride! :)

---

### Post by Penguin360 on 2010-12-09
> **plun said:**
> Why don't you just start in recovery ??

Login

```
startx
```

Update your packages.... fixed packages are at least available from main...probably from mostly all of the mirrors !
I did, and it worked like a charm as far as login is concerned. I also purged the package which is causing the problem. However, after I login, I had a lot of application crash issues. Maybe I will give it another try this weekend, but right now, I don't have time. Thank you for the suggestion.

---

### Post by Penguin360 on 2010-12-09
> **coffeecat said:**
> @CodingBeaver, I have to say that I find this an extraordinary statement. The whole point of alpha and beta testing is to find bugs, discuss them here and report them on Launchpad so that the devs can fix them. Bugs will include things such as failure to login to the GUI - or even worse. I remember a couple of releases ago when python (*again* :rolleyes:) broke badly and many apps, including update manager, wouldn't run at all. That was - er - fun!

If you are running an alpha or beta and not experiencing serious breakages then something is very wrong. It's also very boring.

Enjoy the rough ride! :)

I always tried to jump on using early release of Ubuntu in the past, and I totally agree that the ride is rough but fun. I guess it is too rough for me this time. But I will not give up and will give it another try, maybe this weekend when I have more time. :popcorn:

---

### Post by wilee-nilee on 2010-12-09
I was locked out yesterday like others here I could only get in with the net root in recovery. The sudo service gdm stop command or startx did not work for me.

I just did a net root update/upgrade US severs and I'm back in, I always use auto login anyway.

Had to reload the gnome panel=killall gnome-panel, there was an error with the clock starting, before reloading the panel, I'm using the regular desktop.

May be fixed, hard to say this is development territory.;)

---

### Post by ronacc on 2010-12-09
actually the login issue was an easy fix , see post # 61 , and any of the alphas and in between can blackscreen you .

---

### Post by Penguin360 on 2010-12-09
> **ronacc said:**
> actually the login issue was an easy fix , see post # 61 , and any of the alphas and in between can blackscreen you .

It is not a simple issue for those who only have one computer: no login, no Internet, no Google, no way to find this simple fix.... But I guess those who only have one computer should never try any development release. :p

---

### Post by wilee-nilee on 2010-12-09
> **ronacc said:**
> actually the login issue was an easy fix , see post # 61 , and any of the alphas and in between can blackscreen you .
Post #64
> **ronacc said:**
> thanks for the heads up , purging libcanberra(s) got me back to a crippled desktop but it was crippled before the python updates started , just marking time until the daily's resume and when I get one that boots I'll reinstall .

Lol is all I'm going to say.:popcorn::popcorn::popcorn:

---

### Post by chrismine on 2010-12-09
Don't forget you can use an Ubuntu Live CD to get on to the Internet..
You can also do other interesting things - not applicable but I have used it before to remove viruses from Windows boxes and also delete files that is locked or give Access Denied messages in Windows.

---

### Post by cariboo on 2010-12-09
> **CodingBeaver said:**
> It is not a simple issue for those who only have one computer: no login, no Internet, no Google, no way to find this simple fix.... But I guess those who only have one computer should never try any development release. :p

 We recommend you have a working install along side a testing installation, so that you can fix things by chrooting the broken installation to do updates, fix grub problems and the like. If you only have one computer, running a testing install as your main system, can be a hard thing, especially if you only have a wireless connection. If you have a wired internet connection, you can always start in recovery mode and drop to a netroot prompt.

---

### Post by ronacc on 2010-12-09
> **CodingBeaver said:**
> It is not a simple issue for those who only have one computer: no login, no Internet, no Google, no way to find this simple fix.... But I guess those who only have one computer should never try any development release. :p

they should certainly not use a dev release as their only install . but even with only one computer you can have multiple installs or even install to a usb stick as has been discussed in another thread .If none of the many options are available the just shouldn't run the dev releases .I don't think even the most hard core amongst us advocates courting a real disaster .

---

### Post by Quackers on 2010-12-09
I'm back :-)
I purged the 2 libcanberra packages and then ran updates :-) including a few more libcanberra packages :-) and all is well! I rebooted after the updates and all is still well :-)
Very, very niiiiiiiice :-)

---

### Post by trulan on 2010-12-09
Just updated (via terminal) and the libcanberra packages were among the updates.  I did not purge anything.  I can log in to the desktop again - yay!  Problem solved I guess.

---

### Post by coffeecat on 2010-12-10
> **trulan said:**
> Just updated (via terminal) and the libcanberra packages were among the updates.  I did not purge anything.  I can log in to the desktop again - yay!  Problem solved I guess.

Not so happy here. :( I'd last updated only a couple of hours before this issue struck and chickened out of any updates until now. This morning I did an apt-get upgrade and rebooted. Got past the gdm login screen (hooray!) only to be confronted with a blank purple desktop with a swirling cursor which swirled.... and swirled... and swirled.... Getting bored with this I went to tty1 and tried an aptitude safe-upgrade. A few more packages to be installed including some python 2.6 ones. I thought we were in the middle of an update to 2.7. Ah well. (:sigh: Mine not to reason why.) Allowed that, and rebooted to a blank purple desktop with a cursor that swirled.... and swirled... and swirled....

Fortunately, I'd set the ctrl-alt-backspace kill xserver key combo, so I went back to gdm and logged into the classic desktop. After reloading various panel applets that had failed to load, I had a usable gnome desktop. Logging out and in again to Unity gives me the purple with just an arrow mouse cursor this time. It's boring.

Posting from the Natty classic gnome desktop now. Any thoughts?

I want my Unity back! :cry:

---

### Post by Quackers on 2010-12-10
I haven't had that problem coffeecat. I have just run update and there are, as you say, 3 python2.6 packages available. I didn't install them though, in light of your message. I wonder if these packages are conflicting with something?
Did you try leaving the swirling swirly for a while?

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> Did you try leaving the swirling swirly for a while?

I fell asleep. :wink:

I got this before I installed the python 2.6 packages. Or, at least, I don't remember any python 2.6 packages in the first apt-get tranche of updates. Whatever, I'll sweat this one out till after the 2.6 > 2.7 transition and hope it sorts itself out.

---

### Post by Quackers on 2010-12-10
Lol, I undetstand. You were watching Essex play cricket then :-)
I hope it's not long before it's all fixed up again.
And thanks for the heads up!

---

### Post by cecilpierce on 2010-12-10
Which one is worse ?
(or is it worser)
first is dist-upgrade, then just upgrade.

---

### Post by coffeecat on 2010-12-10
> **cecilpierce said:**
> Which one is worse ?
(or is it worser)

Worse. :) 

<pedantic_mode>
Out of two. Worst of three or more.
</pedantic_mode>

I'd say the first, but who am I to tell? I'm the one with the broken Unity. :|

What were the two commands? I got something really alarming yesterday with 'apt-get dist-upgrade' - which I didn't allow, needless to say.

**Edit:** Actually my trusty Fowler tells me that worser "...has a long literary history beginning in the late 15th century." And then goes on to quote Shakespeare. So you're in good company. :wink:

---

### Post by cecilpierce on 2010-12-10
'sudo apt-get update ; sudo apt-get dist-upgrade' was the first.
Then just 'sudo apt-get update ; sudo apt-get upgrade'
I have 4 natty's and 1 maverick and one of the natty' was broke for a long time, just as I was going to scrap it an upgrade fixed it !

---

### Post by coffeecat on 2010-12-10
> **cecilpierce said:**
> 'sudo apt-get update ; sudo apt-get dist-upgrade' was the first.
Then just 'sudo apt-get update ; sudo apt-get upgrade'

Thanks. I thought it might be. From my experience of yesterday it seems that 'apt-get upgrade' is safer that 'apt-get dist-upgrade', at least at this stage of the development game. Some people prefer 'aptitude safe-upgrade'. I've never used aptitude before now so I might see what each want to do over the next little while.

> **cecilpierce said:**
>  I have 4 natty's and 1 maverick 

Thanks for reminding me. A head cold has turned my brains to mush. I have an as-yet unbroken Natty on my Sony laptop as well, last updated at least two days ago. I'll see what various combinations of apt-get and aptitude offer me.

---

### Post by Quackers on 2010-12-10
I ran an update a couple of days ago which appeared to remove ubuntu-desktop, without any apparent problems. 
If you go to Synaptic and click on Status (bottom leftish) and then on reload, then click on "upgradable" in the left side, all the proposed package changes are listed. If you right-click on the suspect ones and Mark them for Upgrade a box will tell you what it's going to do (ie remove dependencies or refuse to install because of xxx). It may shed some light on things :-)

---

### Post by Harry33 on 2010-12-10
> **Quackers said:**
> ...
I have just run update and there are, as you say, 3 python2.6 packages available. I didn't install them though, in light of your message. I wonder if these packages are conflicting with something?


Those three temporary packages (python2.6, python2.6-minimal, libpython2.6) do not harm in any way, but instead make the transition from python2.6 to python2.7 possible at last.
In addition to those three above, three new dev-packages will be installed (python2.6-dev, libssl-dev, zlib1g-dev).
Soon (depending on your setup) you will be able to remove those 6 packages from your system. You already have three new python packages installed (python2.7, python2.7-minimal, libpython2.7).
In my system, I still need to have new eog and gedit (then again they are already building in launchpad).

By the way: here is the disclaimer from the mainainer:
    "Depend on python2.6-dev for a limited time to
    get packages rebuilt, which depend on python just python-dev,
    but pull in python2.6 by other build-dependencies and fail
    to build by missing header files found in python2.6-dev."

---

### Post by Harry33 on 2010-12-10
> **Quackers said:**
> I ran an update a couple of days ago which appeared to remove ubuntu-desktop, without any apparent problems.
... 


Ubuntu-desktop, ubuntu-standard and ubuntu-minimal are only meta-packages. They only depend on other packages and thus ensure that if they are installed, also the packages canonical wants, are installed.
They can be removed as they actually do nothing.

For example if canonical wants some new application to be included in the default installation, it is added (dependance only) into one of those meta-packages, most likely to ubuntu-desktop.

---

### Post by Quackers on 2010-12-10
Coffeecat, I just ran update again and there's a new Unity package (3.2.6-0ubuntu1)
I wonder if that did the damage? Or maybe repairs it?

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> Coffeecat, I just ran update again and there's a new Unity package (3.2.6-0ubuntu1)
I wonder if that did the damage? Or maybe repairs it?

Thanks. I'm in Maverick atm. I shall have lunch first (you know what they say  about feeding a cold), then reboot into Natty and investigate. I shall report  back. 

Oh, by the way. Forgot to mention...

> **Quackers said:**
> You were watching Essex play cricket then :-)

I only lapsed into a coma when Lancashire came in to bat. :p

---

### Post by Quackers on 2010-12-10
rofl, good luck. I'll be back :-)

---

### Post by Harry33 on 2010-12-10
> **Harry33 said:**
> Those three temporary packages (python2.6, python2.6-minimal, libpython2.6) do not harm in any way, but instead make the transition from python2.6 to python2.7 possible at last.
In addition to those three above, three new dev-packages will be installed (python2.6-dev, libssl-dev, zlib1g-dev).
Soon (depending on your setup) you will be able to remove those 6 packages from your system. You already have three new python packages installed (python2.7, python2.7-minimal, libpython2.7).
In my system, I still need to have new eog and gedit (then again they are already building in launchpad).


Right, I just downloaded eog plus gedit and gedit-common from Launchpad and installed them with dpkg.
After that I was able to say good bye to python2.6. I uninstalled the 6 packages:
python2.6, python2.6-minimal, libpython2.6, python2.6-dev, libssl-dev, zlib1g-dev.

Now my Natty 64-bit has been rebooted and all is well, up and running.

---

### Post by coffeecat on 2010-12-10
Well. Isn't this *fun*? :|

According to Synaptic, my version of unity is 3.2.2-0ubuntu-2, which seems a good bit behind 3.2.6. Whatever. After an apt-get update, apt-get upgrade said:

```
The following packages have been kept back:
  appmenu-gtk computer-janitor computer-janitor-gtk gir1.0-freedesktop
  gir1.0-glib-2.0 hpijs hplip hplip-cups hplip-data indicator-appmenu
  libhpmud0 libnux-0.9-0 libsane-hpaio python python-farsight python-gobject
  python-launchpad-integration python-minimal python-pygoocanvas
  ubuntu-sso-client unity
```And aptitude safe-upgrade said:

```
The following NEW packages will be installed:
  libdbusmenu-glib2{a} libdbusmenu-gtk2{a} 
The following packages will be upgraded:
  appmenu-gtk indicator-appmenu 
```Thanks, fellas. I decided to pass on both and do some investigation first. I tried to update unity only via Synaptic. Sorry results in screenshots. Then I wondered if some personal settings were corrupted, and thought I would create a new user to see. Went to System Administration; No Users and Groups. After much rebooting into Maverick and back again (yes, I could have used the terminal to create a new account) I found that user and groups is part of gnome-system-tools, which was not installed. Quackers, could you check your system? That's an odd omission.

Anyway, created a new user at last, logged into its account to be confronted with the bare purple screen again, so personal settings aren't the problem. It was then I found that the ctrl-alt-backspace combo has to be set for each user, so I had to reboot **again**. Did I mention this was fun? :?

Last shot. I did the aptitude safe-upgrade as above, and then another update and a further aptitude safe-upgrade offered me:

```
The following packages will be upgraded:
  eog evolution evolution-common evolution-plugins gedit gedit-common 
  indicator-me indicator-messages indicator-session indicator-sound 
  libappindicator0.1-cil libevolution libindicate-gtk2 libindicate4 
  python-indicate 
```... which I accepted, but I still can't get into Unity.

Happy days!

---

### Post by coffeecat on 2010-12-10
> **Harry33 said:**
> Now my Natty 64-bit has been rebooted and all is well, up and running.

Which version of Unity do you have?

---

### Post by Amroozy on 2010-12-10
after update i got unity not installed.. when i open Synpatic to install it i got this version 3.2.2-0ubuntu2 when i try to install it i get this message 
unity:
  Depends: libnux-0.9-0 (<0.9.10) but 0.9.10-0ubuntu1 is to be installed

i tried to uninstall libnux and reinstall didn't help to fix it..

---

### Post by Harry33 on 2010-12-10
> **coffeecat said:**
> Which version of Unity do you have?

Hi there,
I am not using Unity at all at the moment. Hence the easyness. :D
After a couple of days ago my Gnome-Shell (from ricotz PPA) died of an incompatibility issue.
New packages of the official repos killed it (the ones like new version of gobject-introspection, GTK+3 and libcanberra).
Now I am using Gnome-Panel.
And I am waiting for Micah Gersten to upload new gnome-shell_2.91.3 into official repos. All the other packages are already there, except gnome-themes-standard.

---

### Post by Harry33 on 2010-12-10
> **Amroozy said:**
> after update i got unity not installed.. when i open Synpatic to install it i got this version 3.2.2-0ubuntu2 when i try to install it i get this message 
unity:
  Depends: libnux-0.9-0 (<0.9.10) but 0.9.10-0ubuntu1 is to be installed
i tried to uninstall libnux and reinstall didn't help to fix it..

Right now the official repos (main server) contain the following and they are installable:
Unity_3.2.6-0ubuntu1
Unity-asset-pool_0.8.18-0ubuntu1
Libnux-0.9-0_0.9.10-0ubuntu1
Nux-tools_0.9.10-0ubuntu1

---

### Post by Quackers on 2010-12-10
Coffeecat, I am currently using Unity 3.2.2-0ubuntu2. The 3.2.6-0ubuntu1 version is the one that is being offered.

I haven't been able to get into users and accounts for a week or more.

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> I haven't been able to get into users and accounts for a week or more.

Interesting. Do you have gnome-system-tools installed?

> **Harry33 said:**
> Right now the official repos (main server) contain the following and they are installable:
Unity_3.2.6-0ubuntu1
Unity-asset-pool_0.8.18-0ubuntu1
Libnux-0.9-0_0.9.10-0ubuntu1
Nux-tools_0.9.10-0ubuntu1

Yes, they are now. Thanks. An hour or so ago unity was blocked by the non-availability of unity-common which is now available. I've upgraded Unity to 3.2.6 (+ dependencies), but that hasn't solved my Unity problem. To be clear: I get the purple wallpaper plus some files I'd dropped onto the desktop while in classic. I also get a standard mouse pointer now which I can move around. But no top panel and no launcher at the side. If I press ctrl-alt-T I get a terminal, ctrl-alt-F1 takes me too tty1 and ctrl-alt-backspace kills the xserver.

As far as I can see all that is missing is the top panel and the dock/launcher. I'd been assuming this was a bug, perhaps in a dependency, but could my system (not personal) settings have got fouled up? What terminal commands do I need to restart the panel and launcher? Thanks.

---

### Post by Quackers on 2010-12-10
I can't even find gnome-system-tools!
You could try killall gnome-panel
Also check that the Unity plugin has not been unchecked in ccsm

---

### Post by Quackers on 2010-12-10
A couple more options in this thread dude :-)

[http://ubuntuforums.org/showthread.php?t=1634486](http://ubuntuforums.org/showthread.php?t=1634486)

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> IAlso check that the Unity plugin has not been unchecked in ccsm

Three steps forward, one step back. Thanks for reminding me about the Unity plugin. It hadn't been unchecked, but I unchecked the 'Float Launcher' option in case that was the problem. It wasn't; it doesn't make any difference.

From the terminal, 'gnome-panel &' gives me the classic desktop panels, top and bottom. In a fit of desperation I tried 'unity' and lo and behold unity unfolded in all its glory. Magic. I even had some [scrunched up paper]("http://ubuntuforums.org/showthread.php?t=1640882") showing in the trash. Cat heaven! However, killing the terminal killed Unity - of course.

If I log in to the broken Unity desktop, do a ctrl-alt-T for a terminal and 'unity &', I get a Unity desktop. If I ctrl-C the process, Unity stays up, but if I close the terminal there's a lot of flickering, the screen goes blank purple for a few moments, and then Unity pops up again. Odd. One problem still is that there are no panel applet icons showing at top right.

I did an aptitude safe-upgrade on my laptop about half-an-hour ago, and it boots quite happily into a perfectly good Unity desktop complete with panel applet icons and scrunched up paper in the trash. Cat paradise!

Very odd. My desktop Unity is broken; my laptop OK. I wonder if there is a gconf setting I need to look at.

> **Quackers said:**
> I can't even find gnome-system-tools!

No, indeed. Looking at my updated laptop install, it doesn't have the gnome-system-tools package installed either. Clearly an omission in the packaging. You need it for the Users and Groups utility.

---

### Post by Quackers on 2010-12-10
Aha! That would answer that then :-) (Users and Groups)
Glad to see that you have semi-recovered :-)
Does Alt + F2 work on yours? Could use that?

---

### Post by cariboo on 2010-12-10
@coffeecat, I have the same problem on one system, the other 4 work the way they should. Intellihide works on all but my netbook, so I'm in the process of creating a bug report.

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> Does Alt + F2 work on yours? Could use that?

I forgot to mention that. No. Just as well ctrl-alt-T works.

> **cariboo907 said:**
> @coffeecat, I have the same problem on one system, the other 4 work the way they should. Intellihide works on all but my netbook, so I'm in the process of creating a bug report.

Thanks. I'll watch out for the bug report and contribute if I can. You know I said that my laptop was working OK? Well now when I switch on I get Plymouth and then it looks as though it wants to load gdm, and then a screen full of text with "panic occurred, switching back to text console", and then further down, "gnome-power-man Tainted", and then even further, "Call Trace:".

Oh joy!

---

### Post by Quackers on 2010-12-10
A kernel panic? Out of my league here :-(

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> A kernel panic? Out of my league here :-(

Normally with a kernel panic, it says 'kernel panic', so I don't know what was panicking here. Anyway, I've found something interesting which you might want to check on your Vaio. The problem seemed inconsistent but I've found the pattern now. If I try to boot my Sony laptop (into Natty) on battery power, I get the above, or I get text messages that suggest filesystem corruption and the bootup stalls beofre the gdm screen. There isn't a filesystem problem - I've done a check from Maverick on another partition. But if I boot up with the power lead in, it boots up just fine into a perfectly good Unity desktop - none of the problems I'm seeing with my desktop machine.

Maverick and Vista boot up on battery power OK so I doubt it's a hardware issue.

While I was investigating this, and before I'd twigged what the problem was, I booted up a couple of times to a recovery console (with the power lead in) to do some updates, and they were coming through think and fast, so I think I'll grab some more updates on my desktop and see if that helps my Unity problem.

---

### Post by Quackers on 2010-12-10
The more updates the better :-)
The problem with the power lead thing was mentioned previously but with a different type of laptop. I'll reboot into Natty on battery and see what happens :-)

---

### Post by Quackers on 2010-12-10
Mine boots up fine into Alpha 1 on battery only.
The white cursor in top left is there for a while but nothing other than that.

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> Mine boots up fine into Alpha 1 on battery only.
The white cursor in top left is there for a while but nothing other than that.

Interesting. I'll look for the other thread. I'm sure mine was booting up OK on battery before today.

---

### Post by coffeecat on 2010-12-10
Another step forward. I don't know which update fixed it, but Unity is starting up by itself now on my desktop machine. But I still don't have the top panel icons. Also, I've just noticed that gnome app menus are not appearing on the top panel as they're meant to, but on the window bar as in classic gnome. So I've got myself a weird hybrid here. I still have to close down from the terminal - no shutdown button.

---

### Post by Quackers on 2010-12-10
Hmm, progress at least :-)
Those odd panel applets problems have all been solved for me for some time.

---

### Post by cariboo on 2010-12-10
> **coffeecat said:**
> I forgot to mention that. No. Just as well ctrl-alt-T works.



Thanks. I'll watch out for the bug report and contribute if I can. You know I said that my laptop was working OK? Well now when I switch on I get Plymouth and then it looks as though it wants to load gdm, and then a screen full of text with "panic occurred, switching back to text console", and then further down, "gnome-power-man Tainted", and then even further, "Call Trace:".

Oh joy!

In my case it seems to be operator error. :) 

Thanks to Omer Akram, who was up well past midnight his time to help me  solve the problem. What I had to do was log out of the Desktop, then log into the Classic Desktop, make sure Effects were turned off, then open ccsm, enable Unity and Autohide, and log out. On logging back into the Ubuntu Desktop, intellihide now works as it should.

---

### Post by coffeecat on 2010-12-10
> **cariboo907 said:**
> What I had to do was log out of the Desktop, then log into the Classic Desktop, make sure Effects were turned off, then open ccsm, enable Unity and Autohide, and log out. On logging back into the Ubuntu Desktop, intellihide now works as it should.

Thanks. As you can see from a couple of posts up, Unity on my desktop has half-healed itself, but I still have a bare upper panel - except for the Ubuntu logo/applications menu launcher, that is. I tried what you suggest, but it didn't make any difference.

Could this be a graphics card/driver issue? Unity is just fine on my Intel graphics laptop. The problem is on this desktop with an ATI Radeon HD4350 with OS driver. It's quite capable - compiz works just fine in Maverick - but compiz is still half-broken in Natty with it. If I try to enable some effects, the launcher disappears, the top window bars disappear and everything becomes unresponsive. So I'm very careful with ccsm. :)

---

### Post by matt_symes on 2010-12-10
Hi guys.

Sorry if i am hijacking this thread for a response or two.

I could do with some direction here as to what you consider is a bug and what you consider is alpha development code instability. I am new to this testing of releases. 

A day after alpha came out i installed it on my laptop on a partition. No problem, i had unity and gnome. I installed the propitiatory drivers (ATI) and, after that, whenever i try unity i get the wallpaper, busy cursor and nothing else. Atl-f2 Nothing. Ctrl-alt-T Nothing. I can drop to consoles ctrl-atl-Fx.. magic keys also work.

I can load Gnome no problem and compiz et al works fine, but window manager is busy when i try to shutdown from GUI after update under gnome. 

I have not got the latest daily builds only updates since install of alpha. Should i try the daily builds and ignore the issues i am having? Are the daily build relevant considering the changes to python over the last couple of days? What should i be concentrating on? Should i reinstall?

I could do with direction for testing. What are your strategies? What are you raising as issues? Is it to early to be raising things?

I think my question is, i am i missing something obvious?

@coffeecat. I blame you. You said come and join the fun ;) And mulord, the jury has the thread if you argue ;)

---

### Post by seenthelite on 2010-12-10
@ matt symes

> I think my question is, i am i missing something obvious? 

My installation is the same as you describe, I am using it in the gnome desktop and will keep updating, it should come good at some stage. I have a nvidia card myself.

---

### Post by Amroozy on 2010-12-11
@matt_symes 
 had most of your problem "the empty screen with busy cursor and window manager not responding when shutdown/restart/logout" i install latest updates as soon as they come out.. and they fixing most of my problems not all... just do the update and never press "partial upgrade button".. if your update manager says no new updates just press the check button.. 
good luck testing

---

### Post by coffeecat on 2010-12-11
> **matt_symes said:**
> @coffeecat. I blame you. You said come and join the fun :wink: And mulord, the jury has the thread if you argue :wink:

I plead guilty, but ask for clemency! :redface:

> **matt_symes said:**
> I could do with some direction here as to what you consider is a bug and what you consider is alpha development code instability. I am new to this testing of releases. 

Sounds like you are getting something similar to what I was getting with the blank wallpaper and swirly cursor, but that's an interesting question. That's what I see as the value of this testing forum. We can discuss issues, see whether other people are getting the same, see if someone has already filed a bug, and so  on.

What?! Ten years' hard labour?  :shock:

---

### Post by rajeev1204 on 2010-12-11
> **coffeecat said:**
> Thanks. As you can see from a couple of posts up, Unity on my desktop has half-healed itself, but I still have a bare upper panel - except for the Ubuntu logo/applications menu launcher, that is. I tried what you suggest, but it didn't make any difference.

Could this be a graphics card/driver issue? Unity is just fine on my Intel graphics laptop. The problem is on this desktop with an ATI Radeon HD4350 with OS driver. It's quite capable - compiz works just fine in Maverick - but compiz is still half-broken in Natty with it. If I try to enable some effects, the launcher disappears, the top window bars disappear and everything becomes unresponsive. So I'm very careful with ccsm. :)


I still cannot login with unity. I did all the upgrades and sitting fine on the desktop with classic gnome.No python breakage as mentioned in sticky but no unity, just a spinning cursor.

I have the fglrx driver installed and works great .Without desktop effects.Visual effects seem to get enabled from the appearance tab but when i reopen appearances, it says 'none'.
But it seems to be enabled since i can see all the compiz effects. 

Probably compiz wasnt properly upgraded since i did the partial upgrade.

---

### Post by trulan on 2010-12-11
> **rajeev1204 said:**
> Visual effects seem to get enabled from the appearance tab but when i reopen appearances, it says 'none'.
But it seems to be enabled since i can see all the compiz effects.
Visual Effects is checked as 'none' here as well (intel i915).  But they are obviously working and enabled as Unity is working (if 3D visual effects are not enabled, Unity won't show up either) and I was able to set Wobbly Windows again.

(I had the Compiz Cube spinning too but you have to kill Unity to get that at this point.)

---

### Post by go7Ul1ai on 2010-12-11
> Probably compiz wasnt properly upgraded since i did the partial upgrade.

 Theres your problem ;)

---

### Post by rajeev1204 on 2010-12-12
My system is completely updated and i still dont have unity .

---

### Post by ronacc on 2010-12-12
lucky you :p

---

### Post by rajeev1204 on 2010-12-12
> **ronacc said:**
> lucky you :p

Unity the desktop i mean.

---

### Post by seenthelite on 2010-12-12
> **rajeev1204 said:**
> Unity the desktop i mean.

Check in Synaptic Package Manager, it may not be installed.

---

### Post by Quackers on 2010-12-12
Also is the Unity plugin enabled in ccsm?

---

### Post by rajeev1204 on 2010-12-13
Well, after all these updates started coming in, i started off with the same symptoms of a wallpaper and the spinning cursor .

I restarted gdm and logged into classic desktop and somehow managed to enable compiz.But i cant seem to enable unity.If i tick the checkbox in the ccsm, window borders disappear and screen hangs.

---

### Post by Quackers on 2010-12-13
I had a similar problem for a while. I think some updates fixed it. I also tried to enable desktop effects and sometimes it would flash the screen and return to "none" but sometimes it would hang for a few seconds and then ask if I wanted to keep the new settings. If I answered yes then compiz and Unity worked ok.
Things are fine now though.

---

### Post by matt_symes on 2010-12-13
> Well, after all these updates started coming in, i started off with the same symptoms of a wallpaper and the spinning cursor .

This is exactly what i have at the moment, although i have not updated for a couple of days.

---

### Post by ronacc on 2010-12-13
go ahead and update this was fixed a couple of days ago also the nm-applet memory leak is much improved .

---

### Post by rajeev1204 on 2010-12-13
> **ronacc said:**
> go ahead and update this was fixed a couple of days ago also the nm-applet memory leak is much improved .

ronacc,my system is completely updated but i still cannot get the unity interface. :(

---

### Post by ronacc on 2010-12-13
probably because compiz isn't starting . it segfaults on me right now .

---

### Post by Harry33 on 2010-12-13
> **ronacc said:**
> probably because compiz isn't starting . it segfaults on me right now .

There is a new version of compiz right now in launchpad done and soon in repos:
&#8220;compiz&#8221; 1:0.9.2.1+glibmainloop3-0ubuntu1

And there will soon be a new unity, right now in dependency wait state in  launchpad because of compiz:
&#8220;unity&#8221; 3.2.6-0ubuntu2

---

### Post by ratcheer on 2010-12-13
My system is now running compiz 1:0.9.2.1+glibmainloop2-0ubuntu4 and unity 3.2.6-0ubuntu1. This is the first time my Natty installation has been running well in about the past four days!

Tim

---

### Post by Yellow Pasque on 2010-12-16
I'm stuck with the looping gdm login. Unfortuantely, this is in virtualbox, so I can't figure out how to get to a tty. RightCtrl+Alt+F1 takes me to a blank black screen and I also can't seem to get to the grub prompt using virtualbox (hitting Esc rapidly after booting doesn't bring it up like it does on a real system) to get to the recovery console.

---

### Post by matt_symes on 2010-12-16
> Unfortuantely, this is in virtualbox

Go on, create a small partition for it. You know you want to ;)

---

### Post by Yellow Pasque on 2010-12-17
> **matt_symes said:**
> Go on, create a small partition for it. You know you want to ;)
I already have a partition with natty on another disk. I don't really feel like rebooting all the time though when I want to do packaging.

---

### Post by Bou on 2011-02-04
Guys,

I tried installing alpha 2 last night but it seems I'm having exactly the same problem described by the OP. Haven't read the whole thread but I see it has the [SOLVED] tag, could you guys summarize what to do to get rid of it?

---

### Post by Harry33 on 2011-02-04
> **Bou said:**
> Guys,

I tried installing alpha 2 last night but it seems I'm having exactly the same problem described by the OP. Haven't read the whole thread but I see it has the [SOLVED] tag, could you guys summarize what to do to get rid of it?

Well that original bug #688013 was about the problems shifting from python2.6 to python2.7.
In the middle of that process gdm was stuck.

Back then, the workaround was this:

1) When login screen appears, press Alt + Ctrl + F1
    This will take you to TTY1
2) Then log in (username and password)
3) Then type: sudo service gdm stop
4) Then type startx

---

### Post by Bou on 2011-02-04
> **Harry33 said:**
> 1) When login screen appears, press Alt + Ctrl + F1
    This will take you to TTY1
2) Then log in (username and password)
3) Then type: sudo service gdm stop
4) Then type startx

I saw a related workaround where you had to start in recovery mode, log in and type startx, but that didn't work (I'll try to ckeck up exactly what error message it gave). As for the login screen, it never really does appear. I always have a black screen with blinking numlock, or the system stops at "checking battery".

---

### Post by Quackers on 2011-02-04
AFAIK the blinking num lock is a kernel panic isn't it?

---

### Post by Bou on 2011-02-06
> **Quackers said:**
> AFAIK the blinking num lock is a kernel panic isn't it?

I think so, yes. Why, is there a way to solve that? :confused:

---

### Post by dino99 on 2011-02-06
> **Bou said:**
> I think so, yes. Why, is there a way to solve that? :confused:

i've needed to remove "quiet splash" to get rid of panic

---

### Post by cecilpierce on 2011-02-06
All three keys blink on mine, I just reboot and it works fine, sometimes I have to reboot two and three times but have not tried to remove quiet splash yet to see if that helps.

---

### Post by Bou on 2011-02-07
> **dino99 said:**
> i've needed to remove "quiet splash" to get rid of panic

Would that be done by rebooting, pressing "e" at grub and then removing the "quiet splash" words, then pressing F10 to boot?

Doesn't seem to work for me :confused:

---

