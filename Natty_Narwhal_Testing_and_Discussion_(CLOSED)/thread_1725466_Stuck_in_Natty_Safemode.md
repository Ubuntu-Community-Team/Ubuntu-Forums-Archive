---
title: "Stuck in Natty Safemode"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by hempanicker on 2011-04-09
Hi friends, 

I'll try and explain the problem that I am face. I'm sure someone can help me out with this.

I use a Compaq Presario CQ62 and was running 10.10 on it.  I had the option of Automatically log in to my account while I was using. Last week, I got this tweet about Natty beta being made available. I just couldn't resist so I installed it on my laptop. (update-manager -d)

I knew it was not stable, but I was ready to play around with it. The upgrade finished and I checked for new updates on update manager 2 times after upgrading to Natty and both the times I got a few more updates to be installed and I installed them. As expected, it was a very unstable version and the new sidebar was invisible. although I could launch applications off it. And it looked like the graphics were really unstable. I thought ill restart the laptop once. The problems started then ! I cannot see anything on Desktop. Its just the wallpaper and nothing else ! the earlier unstable side bar disappeared. I pretty much couldnt do anything with the laptop. But believe it or not, I restarted it 3-4 times, hoping for some miracle to happen and hey it did happen :) Some how I got defaulted on to the safe mode and I got into a seemingly stable desktop, which has many Natty changes, (Banshee Libre Office etc..), but no graphics (as its a safe mode).

Now coming to my real problem :)

Earlier I had mentioned that I had the option of Automatically logging in without prompting a password, thats has gotten me in trouble. Because now I don't get to choose the session, Ubuntu logs in to safe mode. and while im on safe mode I cannot unlock the "login Screen Settings" to disable the auto login.

I'm sure there is a way to do this from command line. I did spend sometime reading through the forums to try and figure out a way to get around this, but didn't have much success. Hope someone can help me here.

please let me know if you need anymore information.
 
(sorry for the lengthy description, I thought its better than just asking a one-liner which will lead to more questions than answers)

---

### Post by wojox on 2011-04-09
See if this still works

```
gksudo gedit /etc/gdm/custom.conf
```

chang AutomaticLoginEnable to false.

---

### Post by hempanicker on 2011-04-09
Thanks wojox. I saw this advice on some other thread too. But I couldn't find such a config file on my system. Do you want me to create one ? If I do, What all should it contain ?


hempanicker@hem-laptop:/etc/gdm$ ls
failsafeBlacklist  failsafeXServer  Init       PostSession  Xsession
failsafeXinit      gdm.schemas      PostLogin  PreSession

---

### Post by hempanicker on 2011-04-09
wojox,

I just created a custom.conf with only the below value

AutomaticLoginEnable=false

and restarted, but still I'm being automatically logged in to Safe mode.


-------------------------------

hempanicker@hem-laptop:/etc/gdm$ ls
custom.conf        failsafeXinit    gdm.schemas  PostLogin    PreSession
failsafeBlacklist  failsafeXServer  Init         PostSession  Xsession
hempanicker@hem-laptop:/etc/gdm$ cat custom.conf 
AutomaticLoginEnable=false

---

### Post by mc4man on 2011-04-09
Not sure why you don't just log out then pick either classic or classic -no effects, then you can try to square up your video driver issues

Ctrl+Alt+SysRq+k

Or just navigate to /usr/share/applications/ and click on Login screen
(if no way to navi then r. click > Create  folder and go from there

Or open a terminal (Crtl+Alt+t) and run gdmsetup

---

### Post by matty abbo on 2011-04-09
couldn't you try booting to the OS in the "recovery boot" and run in fail safe graphics, then ```
sudo apt-get upgrade unity
``` that should sort out the graphics problems

---

### Post by hempanicker on 2011-04-09
> **mc4man said:**
> Not sure why you don't just log out then pick either classic or classic -no effects, then you can try to square up your video driver issues

Ctrl+Alt+SysRq+k

Or just navigate to /usr/share/applications/ and click on Login screen
(if no way to navi then r. click > Create  folder and go from there

Or open a terminal (Crtl+Alt+t) and run gdmsetup
@mc4man Thanks for the reply.

But that is part of my problem, I have this Automatic Login enabled and it will not let me choose the session I want, it just logs in and when I noticed I could find out that the session is "safe mode" hence I am trying to figure out a way to change this automatic login.

I can access my desktop and all menus from within the Safe mode. But when I go to System > Administration > Login Screen (hoping to change the automatic login) I cannot unlock the settings window to even try to change the values.

---

### Post by hempanicker on 2011-04-09
> **matty abbo said:**
> couldn't you try booting to the OS in the "recovery boot" and run in fail safe graphics, then ```
sudo apt-get upgrade unity
``` that should sort out the graphics problems
hempanicker@hem-laptop:~$ sudo apt-get upgrade unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by matty abbo on 2011-04-09
mhmm, thats all i can think of for the graphics playing up, :/

---

### Post by hempanicker on 2011-04-09
> **mc4man said:**
> Not sure why you don't just log out then pick either classic or classic -no effects, then you can try to square up your video driver issues

Ctrl+Alt+SysRq+k

Or just navigate to /usr/share/applications/ and click on Login screen
(if no way to navi then r. click > Create  folder and go from there

Or open a terminal (Crtl+Alt+t) and run gdmsetup
I get the Login window, and when I try to unlock it, nothing happens.

"hempanicker@hem-laptop:~$ sudo gdmsetup
[sudo] password for hempanicker: 

** (gdmsetup:2620): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:2620): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:2620): DEBUG: init delay=30
** (gdmsetup:2620): DEBUG: "/usr/share/xsessions/gnome-classic-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:2620): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:2620): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:2620): DEBUG: Init default session found:'(null)'
** (gdmsetup:2620): DEBUG: Failed to identify the current session: Unable to lookup session information for process '2620'

** (gdmsetup:2620): WARNING **: Unable to find users: no seat-id found
** (gdmsetup:2620): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:2620): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2620): DEBUG: adding monitor for '/home/hempanicker/.face'
** (gdmsetup:2620): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:2620): DEBUG: adding monitor for '/home/test/.face'
** (gdmsetup:2620): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:2620): DEBUG: Found 0 sessions for user test
** (gdmsetup:2620): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:2620): DEBUG: Found 1 sessions for user hempanicker
** (gdmsetup:2620): DEBUG: GdmUserManager: not adding session on other seat: /org/freedesktop/ConsoleKit/Session2
"

---

### Post by mc4man on 2011-04-09
> sudo gdmsetup
don't use sudo

---

### Post by hempanicker on 2011-04-09
> **mc4man said:**
> don't use sudo
hempanicker@hem-laptop:~$ gdmsetup

** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): Key not found
** (gdmsetup:1990): DEBUG: init delay=30
** (gdmsetup:1990): DEBUG: "/usr/share/xsessions/gnome-classic-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1990): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/DefaultSession'): Key not found
** (gdmsetup:1990): DEBUG: Init default session found:'(null)'
** (gdmsetup:1990): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:1990): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:1990): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1990): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1990): DEBUG: adding monitor for '/home/hempanicker/.face'
** (gdmsetup:1990): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1990): DEBUG: adding monitor for '/home/test/.face'
** (gdmsetup:1990): DEBUG: Getting list of sessions for user 1001
** (gdmsetup:1990): DEBUG: Found 0 sessions for user test
** (gdmsetup:1990): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1990): DEBUG: Found 1 sessions for user hempanicker
** (gdmsetup:1990): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session2
** (gdmsetup:1990): DEBUG: GdmUserManager: sessions changed user=hempanicker num=1
** (gdmsetup:1990): DEBUG: GdmUserManager: added session for user: hempanicker

** (ck-history:1998): WARNING **: Unable to parse session removed event: seat-id='Seat1' session-id='Session14' session-type='' session-x11-display='' session-x11-displa1299857851.777 type=SEAT_ADDED : seat-id='Seat1' seat-kind=0

** (gdmsetup:1990): DEBUG: GdmUserManager: history output: hempanic 1790


** (gdmsetup:1990): WARNING **: Unable to lookup user name hempanic: Success
** (gdmsetup:1990): DEBUG: GdmUserManager: history output: test     145

** (gdmsetup:1990): DEBUG: GdmUserManager: history output: gdm      60

** (gdmsetup:1990): DEBUG: GdmUserManager: excluding user 'gdm'
** (gdmsetup:1990): DEBUG: GdmUserManager: history output: guest    2

** (gdmsetup:1990): DEBUG: GdmUserManager: excluding user 'guest'
** (gdmsetup:1990): DEBUG: Login freq 1=0 2=145

** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): Key not found

** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): Key not found

** (gdmsetup:1990): WARNING **: Error calling GetValue('daemon/TimedLogin'): Key not found
** (gdmsetup:1990): DEBUG: init user='(null)' auto=False


I still cannot unlock the Login Screen settings. :(

---

### Post by mc4man on 2011-04-09
This is what my custom.conf looks like after setting to auto then setting back, red would be your username

```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=[COLOR="Red"]doug[/COLOR]
AutomaticLogin=[COLOR="Red"]doug[/COLOR]
TimedLoginDelay=30
DefaultSession=gnome
```

---

### Post by cariboo on 2011-04-09
You have to make sure you don't have auto login set in Users & Groups too. Press Alt-F2 and type user in the search box, the search should find users-admin, click that. Once the window opens up, click the change button beside Password: Not ask on login, then remove the check mark from beside Don't ask for password on login. You should be able to logout and be able to change your session from the login screen.

---

### Post by hempanicker on 2011-04-10
> **mc4man said:**
> This is what my custom.conf looks like after setting to auto then setting back, red would be your username

```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=[COLOR="Red"]doug[/COLOR]
AutomaticLogin=[COLOR="Red"]doug[/COLOR]
TimedLoginDelay=30
DefaultSession=gnome
```
I tried this with my username, with no sucess. It just logs in automatically..

---

### Post by hempanicker on 2011-04-10
> **cariboo907 said:**
> You have to make sure you don't have auto login set in Users & Groups too. Press Alt-F2 and type user in the search box, the search should find users-admin, click that. Once the window opens up, click the change button beside Password: Not ask on login, then remove the check mark from beside Don't ask for password on login. You should be able to logout and be able to change your session from the login screen.
Thanks for your reply cariboo907. However, Alt+F2 is launching the "Run Application" window. Is that where you want me to search for user ? 

I did that anyways and got an error.
"Could not open location 'file:///home/hempanicker/USER'"

May be I'm not doing something right.

---

### Post by 23dornot23d on 2011-04-10
You could always try 

sudo apt-get install kdm

Do whatever you need to do and check that you can get in to your desired mode ok there ....... this is what I do to change systems and set everything up as I want to ...........

I prefer the kdm login menu and choices [COLOR=Red]the gdm login is of no use to me anymore[/COLOR] ...... other than for the auto-login feature ...... ( as kdm does not appear to do this )

( If you get the same problems in kdm then it is maybe your USER setup that has been corrupted )

But by using a different desktop manager it should at least let you know if your settings are ok ..... for the USER or if it is just
a problem with gdm.

________________________________________________________________

Then if you should  want to revert back to gdm for any reason ...... use

sudo-apt-get remove kdm

it will ask you which Desktop Manager you want to use when it uninstall's kdm .....just choose gdm.

---

### Post by cariboo on 2011-04-10
You could always try running:

```
users-admin
```

in a terminal.

---

### Post by hempanicker on 2011-04-10
Tried the last 2 things advised, but with no luck !

I think I should just wait for the official release which is this month anyways. 

Well I got enough warning that this is gonna be unstable, I was too excited to consider that. :)

Anyways, thanks for all your help. Ill keep poking around and will post it here if I somehow figure out a way to do what I was trying to do.

A big thanks to all who read and offered me your, time and advice.

Onwards and upwards !!

Hem

---

