---
title: "hauppage remote problems"
date: 2008-02-02
forum: Mythbuntu
---

### Post by jeffhills on 2008-02-02
Please help! I have posted on 'absolute beginers' with no replies.
I have followed instructions to install Hauppauge Nova T500, I have the remote working on a few buttons, but I cant work out how to istall driver
dev/input and how to get the full lircd.conf file in.
the instruction give the contents of the file, but it does not tell how to install it.
I have googled for hours, please help or point me to a blow by blow instructions page
Jeff

---

### Post by RichardA on 2008-02-03
I've only set up the remote for the Nova-T 500 once, and my notes are scrappy, but in case no one posts a better reply, I think this is what I did:

I might have done these:
Install lirc 8.3
Run 'mythbuntu-lircrc-generator'

I did these:
Choose Hauppauge Nova-T 500 in Mythbuntu Control Centre
In /etc/lirc/hardware.conf, make these changes:
driver="devinput"
device="/dev/input/event5" <- this will be different for you. Do 'dmesg | grep DVB'
I don't think I edited /etc/litc/lircd at all

The page I found most useful was [http://www.parker1.co.uk/mythtv_ubuntu2.php](http://www.parker1.co.uk/mythtv_ubuntu2.php)

Not at all sure about the above, but I hope it's enough to get you started.

---

### Post by jeffhills on 2008-02-03
Richard
Thanks for reply, my problem is when I run
mythbuntu-lircrc-generator
I get
"You should now have a .lirrc file generated in /home/jeffhills/.lircr
Also, a mythtv specific lirrc is now in ~/.mythtv/lirrc"

How do I open the Mythbuntu Control Centre to make changes?
As a complete newby to Linux I have managed to set up a comleat HTPC but I am stuck on this.
the remote works, but only up, down, left, right and the numbey keys work, I thought I only needed to find how to get the lircd.conf file in and I would be up and running, but I cant work out how to do this.
Hope someone can help me.
Jeff

---

### Post by jeffhills on 2008-02-03
Sorry Confusion reigns at this end 
I have Hauppauge Nova-T500  selected in Mythbuntu Control Centre,
I meant how do you open etc/lirc/hardware.conf to make changes,
If I type etc/lirc/hardware.conf  in terminal (as root) i get
"bash: /sudo: No such file or directory"
Thats my real problem, I think I am missing something really basic.
Jeff

---

### Post by RichardA on 2008-02-03
You need to use a text editor to edit the file. 'Nano' is one such -- type 'sudo nano /etc/lirc/hardware.conf' to open the fileas root, there is help on how to save the file at the bottom of the screen. If you're not feeling brave enough for this, use Synaptic to install gedit. Launch it as root with 'sudo gedit' and open the file with File -> Open.

---

### Post by jeffhills on 2008-02-04
Richard
So many thanks. it is ALL working now, it took a bit more reasearch, but the missing "nano" did it. I guess it is so basic none of the guides mention it.
I did not know Linux existed untill about 6 months ago, started playing at Christmas, got a HTPC fully working now.
Many thanks for being the only one of 63 veiws to bother to reply
Jeff

---

### Post by LtPitt on 2008-02-26
This is me being happy!!!

Thanks to your "mythbuntu-lircrc-generator"

NOW MY ATI REMOTE IS WOOORRRKIIINGGG!!!!

YAAY!!!!
YIPPEEEE!!!!

In MythTV!!!

But some buttons are not :(
Like up down left and right...

Any hints?

I'm really CLOSE to heaven now thanks :D

ps
anyone knows about hot use mouse emulation too? :D

---

### Post by majoridiot on 2008-02-27
have you checked this out?  pretty useful, if you don't want to dig through config files by hand:

[http://lircconfig.commandir.com/](http://lircconfig.commandir.com/)

---

### Post by LtPitt on 2008-02-28
Thanks for the help, my friend! :D

I just put the .lircrc file in the wrong folder: it has to be in "home".

Everything is just pefect now =)

I'm just trying to find a way to enable mouse emulation and to load mythtv from the operating system using a button of the controller...
If you have ideas...

I'm happy :D

---

### Post by majoridiot on 2008-02-28
> **LtPitt said:**
> I'm just trying to find a way... to load mythtv from the operating system using a button of the controller...
If you have ideas...

I'm happy :D

you can irexec in /etc/rc.local so it runs as a daemon on login and then put a button definintion
in .lircrc for program irexec, button power and mythvfrontend as the config.  it
would look something like this:

```
begin
        prog = irexec
        button = Power (or the name of the button you want to use)
        config = mythtvfrontend
    end
```

this will not prevent you from running more than one instance of mythfrontend by
mistake, so i connected it to a script that first checks if the frontend is running and
only launches it if there are no other instances running.

i'm currently at work, but can post the relevant info for you to adapt, once i get home.
it's really not too tough to figure out, tho... and is a great learning experience ;)

EDIT: here is the info:

edit /etc/rc.local as sudo and add the following before the existing "exit 0":

```
irexec -d
```

then add the following button definition to your .lircrc file, making sure the name of the remote and button are what you need them to be:

```
begin
    remote = mceusb
    prog = irexec
    button = Power
    config = launch_frontend.sh &
end
```

next, create the launch_frontend.sh script with the editor of your choice and save it in your home directory:

```
#!/bin/sh
if ps -A | grep "mythfrontend"
then
  exit 1
else
  mythfrontend 
fi
exit 0
```

make it executable, and copy it to /usr/bin:

```
$ chmod +x launch_frontend.sh
$ sudo cp launch_frontend.sh /usr/bin
```

logout, log back in and test it.

---

### Post by LtPitt on 2008-02-29
Omg.

I could not dream anything better :|

I still have to test that but you've won a dinner in Rome, whenever you want.

THANKS TRUELY A LOT! :D

you made my mediacenter real! :D

(and my life better)

---

### Post by majoridiot on 2008-02-29
> **LtPitt said:**
> Omg.

I could not dream anything better :|

I still have to test that but you've won a dinner in Rome, whenever you want.

THANKS TRUELY A LOT! :D

you made my mediacenter real! :D

(and my life better)

i seriously hope you do not mean rome, alaska ;)

---

### Post by LtPitt on 2008-03-01
hahahahha I wish I could get there sometimes but I'm stuck in the middle of Italy!

I'LL BE YOUR WORST NIGHTMARE:

with what I've learnt here I felt like a little god and thought:
"wow! I can ALSO shutdown the computer from my bed. that's breezy!"

So I started messing.

I've found out that:

a) the shutdown command's a bith. it needs the sudo password. and irexec, runnning in backgound, doesn't give any feedback. So I went crazy for hours until I ran it from terminal and found this thing out.

b) so i made another .sh script with sudo shutdown -h in it. no luck.

c) I did sudo visudo to change all to no password for all users in the world. no luck

d) I started to inhale gas from my kitchen

any (final, I promise) hint? :'(

---

### Post by majoridiot on 2008-03-01
> **LtPitt said:**
>  b) so i made another .sh script with sudo shutdown -h in it. no luck.

c) I did sudo visudo to change all to no password for all users in the world. no luck(

in your shutdown script, try the shutdown command:

```
sudo shutdown -h -P now
```

then **sudo visudo** again, and add:

```
%LOGIN_NAME ALL=NOPASSWD: /sbin/shutdown
```

replace <LOGIN_NAME> with your user name for that box, 
give it a shot and see how it goes!

---

### Post by LtPitt on 2008-03-01
I already tried a more aggressive solution:

a) I made my user part of the root group

b) I've added in sudoers

root ALL=(ALL) NOPASSWD: ALL

and to be absolutely sure:

myusername ALL=(ALL) NOPASSWD: ALL


Same error :|

no output when I just click the button and if I click the button while in a terminal I run irexec to see the output I get "you need to be root to shutdown".

oh
my
god.

:|

---

### Post by LtPitt on 2008-03-01
and there's more!

if I run my script this way:

./myscript


the computer shuts down...

if I use the remote everything is as described in the previous post :|

---

### Post by majoridiot on 2008-03-01
> **LtPitt said:**
> if I run my script this way:
./myscript
the computer shuts down...
if I use the remote everything is as described in the previous post :|

permission-wise, all you should need to do is the viduso with: 

```
%LOGIN_NAME ALL=NOPASSWD: /sbin/shutdown
```

try copying your shutdown script to /usr/bin:

```
$ sudo cp myscript /usr/bin/
```

i've found that irexec likes scripts in the system path, like the launch frontend script you did earlier.

---

### Post by LtPitt on 2008-03-01
I've found the problem finally: I'm stupid :D

When I start my computer I run irexec.

Now I'm running it using sudo irexec.

Strangely everything works great! :D :D :D

True thanks for your infinite patience and effort.

I HAVE A MEDIA CENTER.

:D

---

