---
title: "Afghanistan keyboard instead of UK???"
date: 2011-01-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-01-06
I have just run today's updates, which included 2.6.37-12 kernel. The kernel upgrade reported an error and said that due to a problem it would remain unconfigured. It rebooted fine though, and currently shows that the kernel being used is v.12, so whatever :confused:
What is a mystery, is that after a reboot my caps/lock/num lock lights were stuck on and the new keyboard applet shows I am on US keyboard. So after cycling the caps lock it goes to Afghanistan keyboard (which works as a UK keyboard). Cycling again turns the caps lock lights off and the applet says it's a UK keyboard. But it isn't, it's back to US again!
So, in other words, for the keyboard to be a UK layout, which is what I want, the caps lock lights have to be on.
Anybody else finding this?

---

### Post by Harry33 on 2011-01-06
> **Quackers said:**
> I have just run today's updates, which included 2.6.37-12 kernel. The kernel upgrade reported an error and said that due to a problem it would remain unconfigured. It rebooted fine though, and currently shows that the kernel being used is v.12, so whatever :confused:
What is a mystery, is that after a reboot my caps/lock/num lock lights were stuck on and the new keyboard applet shows I am on US keyboard. So after cycling the caps lock it goes to Afghanistan keyboard (which works as a UK keyboard). Cycling again turns the caps lock lights off and the applet says it's a UK keyboard. But it isn't, it's back to US again!
So, in other words, for the keyboard to be a UK layout, which is what I want, the caps lock lights have to be on.
Anybody else finding this?

I did the new kernel upgrade today too, with no errors.
But I do not have the issue you described.
Natty 64-bit.

---

### Post by dino99 on 2011-01-06
hm, might not be a bug but a ghost :(

the new kernel 12 today has been installed with a new xserver & keyboard-configuration. On my system installing these packages i've been asked about such keyboard custom settings taking control over console-setup. Maybe reconfigure keyboard-configuration (new package)

---

### Post by Quackers on 2011-01-06
I'll do some mooching about and see what I can come up with :-)
I was asked about configuring the keyboard during the upgrade. I ok'd the default. Maybe not such a good idea, then!
Thanks people.

---

### Post by nm_geo on 2011-01-06
> **Quackers said:**
> I have just run today's updates, which included 2.6.37-12 kernel. The kernel upgrade reported an error and said that due to a problem it would remain unconfigured. It rebooted fine though, and currently shows that the kernel being used is v.12, so whatever :confused:
What is a mystery, is that after a reboot my caps/lock/num lock lights were stuck on and the new keyboard applet shows I am on US keyboard. So after cycling the caps lock it goes to Afghanistan keyboard (which works as a UK keyboard). Cycling again turns the caps lock lights off and the applet says it's a UK keyboard. But it isn't, it's back to US again!
So, in other words, for the keyboard to be a UK layout, which is what I want, the caps lock lights have to be on.
Anybody else finding this?

I did get the same statement about the 2.6.37-12 kernel and went ahead and filled out the bug report.  I did state that it appeared to be a timing issue and that the kernel did install okay.  I now also have the strange keyboard Icon on top too.

---

### Post by nm_geo on 2011-01-06
Hmmm.. meant to show screen shot

---

### Post by arpanaut on 2011-01-06
Pardon the Interruption.

But, why do I want or need the keyboard icon on my panel?
I thought we were moving to simplicity and less clutter.
I have never used any other keyboard set up other than my default USA, probably never will.
I'm sorry but I do not understand this addition!

I also ended up with a bottom panel after todays upgrades... easily solved but why?

---

### Post by coffeecat on 2011-01-06
Just did about 100MB of updates including the -12 kernel. Got the kernel error message as others have, but no apparent problems after reboot. I was prompted with a "Configuring keyboard-configuration" (interesting tautology - configuring a configuration) window twice during the dpkg process - I was using Synaptic for the update. The first time it defaulted to the UK keyboard layout which I accepted, the second to Afghanistan which I changed to UK. And the keyboard seems to have stayed on UK for me. Let's see: £££. Yup. UK. :)

But I didn't get the keyboard icon in the panel - which I would like. :confused:

---

### Post by nm_geo on 2011-01-06
> **coffeecat said:**
> But I didn't get the keyboard icon in the panel - which I would like. :confused:
 
I will trade you my Icon for your Avatar. :p
 
Not really.. Allergies you know but I like that cat.

---

### Post by Quackers on 2011-01-06
When I first rebooted I had a bottom panel and the dodgy keyboard/caps lock light problem. After another reboot the bottom panel disappeared. After a couple of later updates I shut the laptop down, as I went out. I have now fired it up and the bottom panel was back and my caps lock/num lock lights are on again.
I ran a couple of updates just now, and rebooted. The bottom panel is now gone again and my keyboard came back on US settings and the caps lock/num lock lights are on.
I've changed the keyboard applet to UK again and the keyboard has stayed on UK settings (£ " @ ) yep, still on UK - but the lights are still stuck on!
Weird!

---

### Post by cariboo on 2011-01-06
There was something in the keyboard preferences setup up about caps lock, I just left it and clicked forward, and haven't had a problem. I got rid of the keyboard icon by deleting Afghanistan from the keyboard preferences.

---

### Post by arpanaut on 2011-01-06
Very Interesting.

Previous comment refers to my Mav->Natty upgraded install and haven't rebooted to it yet.
Now I'm on my pure Alpha1 install and got all the keyboard rigmarole and kernel config errors but upon reboot no keyboard icon in panel and no bottom panel.

I guess I'm going to have to do a fresh install from the daily just to see what happens. LOL
Been putting it off for a week or so, now I have a good reason.
I'm getting impatient for Alpha2...

> I got rid of the keyboard icon by deleting Afghanistan from the keyboard preferences.Thank you very much!

---

### Post by Quackers on 2011-01-06
> **cariboo907 said:**
> There was something in the keyboard preferences setup up about caps lock, I just left it and clicked forward, and haven't had a problem. I got rid of the keyboard icon by deleting Afghanistan from the keyboard preferences.

I did the same cariboo907. Which keyboard is your default choice, please?

---

### Post by nm_geo on 2011-01-06
> **Quackers said:**
> I did the same cariboo907. Which keyboard is your default choice, please?

I knew I would not be using Afghanistan keyboard and did the same now Icon is gone from top panel.  Guess there will be no trade with coffeecat.

---

### Post by nm_geo on 2011-01-06
Logged out and back to classic desktop and guess what I found the crazy little keyboard icon and of course Gnome panels bottom and top. Quackers you might check under Layout/options I noticed a Use keyboard LED to show alternate layout.

---

### Post by Quackers on 2011-01-06
> **nm_geo said:**
> Logged out and back to classic desktop and guess what I found the crazy little keyboard icon and of course Gnome panels bottom and top. Quackers you might check under Layout/options I noticed a Use keyboard LED to show alternate layout.

Yes :-) That did the trick :-) Oh happy day!
I made UK the default and turned off those pesky lights in the options and voila! UK keyboard, GBR displayed in the applet and no pesky caps lock/Num lock lights. 
Very very niiiiiiiiice :-)
Thank you nm_geo!

---

### Post by nm_geo on 2011-01-06
You are welcome.. Glad it worked.  Now I am loading up the Unity panel and smashing the trash can..:lolflag:

It really looks crazy. 17 icons stacked in the panel.

---

### Post by Quackers on 2011-01-06
17 icons? Are you sure you're not looking at the trash can? :-)

---

### Post by nm_geo on 2011-01-06
> **Quackers said:**
> 17 icons? Are you sure you're not looking at the trash can? :-)

I am locking Icons in the Unity Panel to see how it responds have 18 now.

---

### Post by nm_geo on 2011-01-06
Here is a screenshot of the smashed trash can.

---

### Post by Quackers on 2011-01-06
It looks like it's been trodden on :-)

---

### Post by nm_geo on 2011-01-06
Yes is does look trodden on. The cool thing is if you mouse over  the panel all icons becomes normal sized icons and they move above and below the screen then you can use your mouse and scroll up or down to pick the one you want.  Maybe I will put all my applications in the unity panel.. Naw probably not..:lolflag:
But I might see how many it can hold above 18 just for fun.

---

### Post by cecilpierce on 2011-01-06
How did you guys get rid of the gnome-panel ?
Mine is at the bottom.

---

### Post by nm_geo on 2011-01-06
In terminal 

```
ps -A |grep panel
```

then paste results

---

### Post by cecilpierce on 2011-01-06
I tried to kill it but it comes right back.

---

### Post by nm_geo on 2011-01-06
Try this ```
kill `pidof gnome-panel`
```If that does not work get mean LOL

```
kill -9 `pidof gnome-panel`
```I believe that will stop the process and if you want them back you can do that too. I just tested mine with unity on I started the gnome panel and killed it.

---

### Post by cecilpierce on 2011-01-06
Tried both, it goes away for a couple seconds and come back :mad:

---

### Post by nm_geo on 2011-01-06
> **cecilpierce said:**
> Tried both, it goes away for a couple seconds and come back :mad:

If you copied and pasted those little ` are not single quotes. Then something is restarting the gnome panel and you are logged in the Desktop mode not classic right?

---

### Post by gajuambi on 2011-01-06
Hi
trying to install ubuntu from the past one 1.5 years but no go..
Newbee to ubuntuforums...where can i ask a question?
Or 
start my own thread?
Or
create new post?

---

### Post by cecilpierce on 2011-01-06
> **nm_geo said:**
> If you copied and pasted those little ` are not single quotes. Then something is restarting the gnome panel and you are logged in the Desktop mode not classic right?

Right, Desktop Edition, not Classic. I tried logging out and back in, this panel came up yesterday after updates.

---

### Post by nm_geo on 2011-01-06
> **cecilpierce said:**
> Right, Desktop Edition, not Classic. I tried logging out and back in, this panel came up yesterday after updates.

Those work for me they stop the process and unless I restart the gnome panels do not appear.

---

### Post by nm_geo on 2011-01-06
> **gajuambi said:**
> Hi
trying to install ubuntu from the past one 1.5 years but no go..
Newbee to ubuntuforums...where can i ask a question?
Or 
start my own thread?
Or
create new post?

Hi gajuambi ..
Yes a new topic in Absolute Beginner Talk forum would be best 
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by mc4man on 2011-01-06
> Right, Desktop Edition, not Classic. I tried logging out and back in, this panel came up yesterday after updates.

Well i did a completely new install today (was getting 50/50 kernel panics over the last few weeks), and did notice that once and a while a logout/in would load gnome-panel for some reason. (in the Desktop login.

If you can't resolve you could probably login to the Classic and remove the lower panel.
Then if gnome-panel is loaded in the Desktop login you shouldn't see the bottom panel anymore (the top panel will still be there, but unless you use rotate cube you'll never see it.

(at this point you could also just run unity thru the Classic login, not sure if there is any downside other than using a different profile and a few extra process's, - a couple of things that are currently no go in desktop would work - Alt+F2 for ex.

---

### Post by cecilpierce on 2011-01-06
Thanks for the info, for now I'll just use Autohide and wait and see what happens.

---

### Post by coffeecat on 2011-01-07
> **coffeecat said:**
> But I didn't get the keyboard icon in the panel

> **nm_geo said:**
> I will trade you my Icon for your Avatar. :p

> **cariboo907 said:**
> I got rid of the keyboard icon by deleting Afghanistan from the keyboard preferences.

> **nm_geo said:**
> now Icon is gone from top panel.  Guess there will be no trade with coffeecat.

Thanks! :) Now I've got the icon in the panel by adding UK Macintosh to Keyboard layouts and I have the choice between UK standard and UK Mac. Which is actually quite useful for me. I have my Ubuntu/W7 machine and a Mac Mini connected to peripherals through a KVM switch and I can never finally decide whether to use my Logitech or Mac keyboard - there are significant differences between them in UK versions. Either I hobble MacOS or I don't have a SysReq key in Ubuntu - which can be a bit of a necessity when alpha testing. At least now I have a bit more flexibility in Ubuntu.

---

### Post by MacUntu on 2011-01-07
> **cariboo907 said:**
> I got rid of the keyboard icon by deleting Afghanistan

Isn't that a bit offending? :lolflag:

---

### Post by dino99 on 2011-01-07
the latest xserver-common 902-1ubuntu4 might have solved this issue (when ctrl+shift was set as custom switching)

---

### Post by rburkartjo on 2011-01-07
car tks removing the afg keyboard from the pref also worked for me

---

### Post by Quackers on 2011-01-07
Lol, my bottom panel is back again :-) It will probably disappear when I next reboot!
Logging in to classic doesn't allow me to delete the panel any more! Strange occurences!
Nevermind, it will disappear when it's ready :-)

---

### Post by cecilpierce on 2011-01-07
> **Quackers said:**
> Lol, my bottom panel is back again :-) It will probably disappear when I next reboot!
Logging in to classic doesn't allow me to delete the panel any more! Strange occurences!
Nevermind, it will disappear when it's ready :-)

It sure is aggravating, I have 4 Natty's and one doesn't have the panels, can't find the difference.

---

### Post by Quackers on 2011-01-07
I have 2 Nattys and the bottom bar comes and goes at will on both installations. It will almost certainly disappear if I reboot now. It's a lottery :-)

---

### Post by cecilpierce on 2011-01-07
Autohide the dang bar, out of site, out of mind !!! :D

---

### Post by Quackers on 2011-01-07
> **cecilpierce said:**
> Autohide the dang bar, out of site, out of mind !!! :D

An excellent idea! I may resort to that if it really starts to bug me :-)

---

### Post by MickeA59 on 2011-01-14
Hi there 
Have a Swedish keyboard ... no luck what so ever to get it working ... wich package do i have to re/configure to get it working

---

### Post by garvinrick4 on 2011-01-14
#Keyboard in Applications.
#layouts
Options to Keys to change layouts if Cap lock's does not work, uncheck it. If have more
than one keyboard choosen the default was to have Caps lock change
between the keyboards choosen when new keyboard package installed.
Applet will leave if just one keyboard config choosen.

---

### Post by JRV on 2011-01-14
On my main system (Lucid) it started defaulting to a Spanish keyboard layout that I did not install a couple of days ago. (Easily fixed) 

My Natty test system loaded the Afghanistan keyboard layout, but left the US keyboard as the default.

Is this a bug that affects more than Natty?

---

### Post by garvinrick4 on 2011-01-14
> **JRV said:**
> On my main system (Lucid) it started defaulting to a Spanish keyboard layout that I did not install a couple of days ago. (Easily fixed) 

My Natty test system loaded the Afghanistan keyboard layout, but left the US keyboard as the default.

Is this a bug that affects more than Natty? I have all from 9.10 up to 11.04 and only natty has this. Do not know if was or is a bug, it was at install of package asked what you want to use to switch keyboards and default or first choice was Cap locks. Afghanistan I assume is the first keyboard alphabetically so uses it and your keyboard of choice at install. Must have been a way not to install another keyboard that I missed. Easy fix though as previous post.

---

### Post by moviemaniac on 2011-01-18
My main machine defaults to the US layout every time I reeboot now (I have a German Apple keyboard...). Very, very annoying. I think it was the keyboard-configuration package which srewed things up...

---

### Post by Quackers on 2011-01-18
I'm still having the odd problem with it. Sometimes on reboot it will default to US keyboard and the caps lock light is on. I can't count how many times I have cancelled the caps lock in Layout > options. 
Sometimes the top panel will show USA keyboard, but it isn't, it's a UK keyboard. It's quite a mess.

---

### Post by dino99 on 2011-01-18
have tested with localepurge ?

---

### Post by dino99 on 2011-01-18
have tested with localepurge ?

---

### Post by Quackers on 2011-01-18
What's localepurge please?

I just rebooted and it's showing USA keyboard and the caps lock is on. I pressed the caps lock and the light went out but the keyboard is showing as USA in the top panel, but it isn't, it's a UK board. I even tried deleting the USA keyboard but it just comes back :-) like a boomerang.

---

### Post by Peter09 on 2011-01-18
I am getting the same problem except mine is UK and USA keyboard. Just cannot get of the USA keyboard in the panel, although the actual keyboard in use is the GB one.

---

### Post by philinux on 2011-01-18
> **Peter09 said:**
> I am getting the same problem except mine is UK and USA keyboard. Just cannot get of the USA keyboard in the panel, although the actual keyboard in use is the GB one.

Change the prefs on the login screen. I still don't get the need for a panel applet for this though. Hopefully it will disappear in time.

---

### Post by Quackers on 2011-01-18
I think the panel applet is half the problem :-) Sometimes I can't change the applet from displaying USA even though the keyboard is UK. It's just not working imo.

---

### Post by Quackers on 2011-01-18
I've found another problem with this sfotware (just confirmed).
If my laptop is left on for a few hours, being used sporadically in that time, the keyboard completely reverses the caps lock setting. I am typing this in lower case by holding down the shift key while typing. THIS IS WHAT HAPPENS WHEN I DON'T DO THAT.
There is no caps lock on and no keyboard lights on. The only way to cure this, now that it has happened, is to reboot. Then it will be fine again for a few hours.
There doesn't seem to be a specific cause other than the time element.
Any body else finding something similar?

Can this applet and its corresponding program be uninstalled? I don't even want it. I can't remember its name :-(

---

### Post by buzzmandt on 2011-01-18
Kubuntu is subject to this as well.

---

### Post by garvinrick4 on 2011-01-19
#Applications to Keyboard to Layouts to Options to Key(s) to change layout to
uncheck capslock.
#That is if you want Capslock to go back to normal behavior.

---

### Post by Quackers on 2011-01-19
> **garvinrick4 said:**
> #Applications to Keyboard to Layouts to Options to Key(s) to change layout to
uncheck capslock.
#That is if you want Capslock to go back to normal behavior.
Thanks for the suggestion garvinrick4, but I do that after every boot or reboot. I have to do that to get the caps lock/scroll lock lights to go out. I unset the settings in Layout/Options and they come back. Every time! It gets quite annoying :-)
I'd really rather get rid of it completely, but the package seems to want to remove a LOT of dependencies, so I guess I'm stuck with it now :-(

---

### Post by garvinrick4 on 2011-01-19
> **buzzmandt said:**
> Kubuntu is subject to this as well.
Use my previous post:
When the keyboard app installed the default was adding the first keyboard in
list alphabetically. So you got Afghanistan and your install choice and uses Capslock
as default when it was installed in upgrades. Use previous post and will remove
from upper panel and be alright. When you have more than one choice it adds itself
to unity panel.
### Remove Afghanistan keyboard in layouts.

##When have more than one keyboard choice have to select what key commands to switch from one to another.
Now is set at Caps locks I do believe that was default but are more .

---

### Post by garvinrick4 on 2011-01-19
> **Quackers said:**
> Thanks for the suggestion garvinrick4, but I do that after every boot or reboot. I have to do that to get the caps lock/scroll lock lights to go out. I unset the settings in Layout/Options and they come back. Every time! It gets quite annoying :-)
I'd really rather get rid of it completely, but the package seems to want to remove a LOT of dependencies, so I guess I'm stuck with it now :-( If have more than one keyboard in selection there is a variety of different key commands to switch between the keyboards, selection was at install from upgrades in unity. The first one in order was Caps locks but their are more. Look into the settings in keyboard app or just use one keyboard remove in the layouts tab.

---

### Post by Quackers on 2011-01-19
Thanks again. But I must be missing something.
5 minutes ago I cancelled the caps lock/screen lock lights in Layout/Options as in first screenshot. I also tried to delete USA keyboard but it just comes back.
I've just been back in to Layout/Options and they're back again! Please see attached.

---

### Post by garvinrick4 on 2011-01-19
#I highlighted my second choice keyboard and hit remove:
#I unchecked the Capslocks in Key(s) to change layout and applet left the upper panel:
#When I was hitting Capslock I was typing in Afghanistan which
was the second keyboard which I removed. Afghanistan was put
in when application keyboard was upgraded in unity because first in line alphabetically. 
I did not select Afghanistan keyboard must have been a selection that I did not see.
It seems a lot of users have the Afghanistan keyboard also needing to be removed.
#The first screenshot you are showing I did not have to touch.

## I do not know if the keyboard you choose at install is the one that has to be the
only keyboard in selections and is not removable.

---

### Post by Quackers on 2011-01-19
I have deleted the Afghanistan keyboard without problem. I have tried to delete the USA keyboard option and it disappears, but the next time I open the applet it's back. The same thing is hapening with the caps lock and scroll lock check marks in the Layout/Options screen. I must be missing something, but I don't know what.
Whatever I do the applet always stays in the top panel.

---

### Post by garvinrick4 on 2011-01-19
#The Afghanistan keyboard removal seems to remove the applet. 
#Is it something that is only buggy with the USA and UK keyboard selections? 
#You did reset to default?
#Would be worth a check in lauchpad.
#Sorry did not help you Quackers could be a bug you found.

---

### Post by Quackers on 2011-01-19
Hmm, maybe mine is different then. The Afghanistan keyboard was deleted successfully a few days ago, but my applet is still in the top panel. In fact, I can't get rid of it :-)
I've also tried to remove the USA keyboard but that won't go. Maybe that has to be there, I don't know.
Thanks again for the suggestions sir :-) I'll see how things go and see whether other users are finding similar problems.

---

### Post by moviemaniac on 2011-01-19
found a fix:

sudo dpkg-reconfigure keyboard-configuration

set the options as needed. (you can also disable the capslock-annoyance-thingy).
Afterwards it *should* build a new initramfs automatically (I had to do it manually since I don't use Ubuntu's kernels). If not, do it manually (sudo update-initramfs -c -k [insert kernel revision here without these brackets ie 2.6.27-12])
Reboot and the problem's gone.

---

### Post by Quackers on 2011-01-19
> **moviemaniac said:**
> found a fix:

sudo dpkg-reconfigure keyboard-configuration

set the options as needed. (you can also disable the capslock-annoyance-thingy).
Afterwards it *should* build a new initramfs automatically (I had to do it manually since I don't use Ubuntu's kernels). If not, do it manually (sudo update-initramfs -c -k [insert kernel revision here without these brackets ie 2.6.27-12])
Reboot and the problem's gone.

I just ran this and..........I'm cautiously optimistic :-)
The applet is still in the panel, but it's showing GBr and it's typing like a UK keyboard and I have no keyboard lights on after a reboot :-)
That's good!
Thanks moviemaniac, you've been a big help!

---

### Post by moviemaniac on 2011-01-19
Well, I guess the applet's a new feature as it's not a standalone-applet but it's integrated in the canonical-status-bar-thingy which also shows the volume setting and such.
It's the packaging of the program that's borked - when you update via GUI you only get to set one option (the capslock thing) and another bug would be the default keyboard-configuration-program not storing the settings anymore.

---

### Post by garvinrick4 on 2011-01-19
#I have know applet, it  was removed when deleted afghanistan keyboard but it
still seems to show in default keyboard config as below and caps_toggle also of 2 installs.
#Must make default keyboard settings at install of keyboard-configuration in
Unity I also find know independent applet in system. Lots of changes most likely
coming. 
#Are you making a new /etc/default/keyboard when reconfiguring keyboard?
#My installs working fine so do not want to run fix.
#That is a nice fix to rebuild config file.

###rick@rick-HP:~$ cat /etc/default/keyboard
# If you change any of the following variables and X is configured to
# use this file, then the changes will become visible to X only if udev
# is restarted.  You may need to reboot the system.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="a4techKB21"
XKBLAYOUT="us,af"
XKBVARIANT=","
XKBOPTIONS="grp:caps_toggle,grp_led:scroll"

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
rick@rick-HP:~$

---

### Post by Quackers on 2011-01-21
For some unfathomable reason, after using my keyboard for a few hours (on and off) the applet displays GBR but the actual keyboard types US characters. If I change the layout in the applet, the display changes to USA and the keyboard still types US characters. If I then change the applet again to GBR, the keyboard then changes to GBR keyboard, but the display stays on USA in the applet. Just like it is now, actually!
Something's not working.
And this is after I ran moviemaniac's fix again, after installing the second keyboard-config update.
Bit of a shambles I think.

---

### Post by Peter09 on 2011-01-22
Try changing the keyboard at the 'login screen' at the bottom, this appears to be a permanent fix (it was for me anyway).

---

### Post by cariboo on 2011-01-28
Here's an update from Colin Watson, on this problem:

> Lots of people have reported keyboard layouts being broken in Natty in
one way or another.  This was due to a merge I did from Debian on
2011-01-05 which worked fine in my tests, but turned out to fail in a
number of common cases.  I've identified two major problems:

 * I added some misguided migration code which broke in the case of
   debconf preconfiguration (which most people use because apt does it,
   but I was testing with 'dpkg -i').  The effect of this was to reset
   the various keyboard settings to the first choice in their respective
   lists: if you have XKBMODEL="a4techKB21" and XKBLAYOUT="us,af" in
   /etc/default/keyboard, then this is what happened.  This also tended
   to result in keyboard questions being asked on every upgrade.

 * Versions of the installer-side keyboard handling code prior to Natty
   didn't always set the 'seen' flag for keyboard questions in the
   installed system's debconf database.  As a result, many people were
   asked the keyboard layout and variant questions again.

I've uploaded console-setup 1.57ubuntu5 to fix this.  When upgrading the
keyboard-configuration package to the new version, if it detects a
migration bug, it takes the old commented-out XKB* values from
/etc/default/console-setup and restores them, which should restore the
correct keyboard layouts for most people.  It will print messages on
standard error saying that it is doing so, but will not present any
debconf messages.

However, if you installed your system with an image from before
2011-01-05, upgraded it to current Natty, and then manually edited
/etc/default/keyboard or used 'dpkg-reconfigure keyboard-configuration',
the effect of this cleanup will be to *erase* those manual changes and
restore the configuration from before you upgraded console-setup.  I
hope that this will cause few problems, as the overwhelming likelihood
is that the previous configuration was more accurate.  I considered
presenting the debconf questions again, but given the significant
confusion already caused I felt that this would not improve the
situation.

Note that all of this only affects people who have upgraded through
Natty between Alpha 1 and Alpha 2.

If there's still a problem after all this, please let me know.  Sorry
for any inconvenience caused!


---

### Post by Quackers on 2011-01-28
Thanks for that info cariboo907.

---

