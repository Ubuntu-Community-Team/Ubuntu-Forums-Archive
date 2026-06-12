---
title: "ISO Testing Free Software only install"
date: 2010-12-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Wobblybob on 2010-12-02
hi, as the UK has come to a halt due to a bit of snow I thought I'd do some iso testing. 

I've chosen to start with the first case on the ISO Testing tracker [http://iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/"), the Free Software only install. The test PC has an nVidia card so I expected a 2d desktop and got one with the following message.

> Information:
Sorry you don't have 3d support, install it for
your graphic hardware to get Unity or please
reboot and select "Classic session" at startup.

Which is fine, as it's a free software install I would not have the option or want to add restricted drivers so should only have the 2d DT. The question is the message states "please reboot and select "Classic session" at startup" but How?

I have a Grub startup which shows no other option and the logon which again gives no option and when I get to the DT I get the same message. I assume that if I could login as a classic session it would remove the message. Is this a bug or a feature?

I know I can go into [System], [Administration], [Login Screen] and change [Ubuntu desktop Edition] to [Ubuntu Classic Desktop] but this is not obvious from the message box and a new user would struggle to find it.

---

### Post by cariboo on 2010-12-02
Just to let you know, you can still use free software only and have 3D by installing libgl1-mesa-dri-experimental, it's in the repositories.

For your other matter, I hope you created a bug. The devs have decided that the default should be the Ubuntu Desktop, which I personally don't agree with. I would prefer it default to the Classic Desktop, so that those of us that need extra drivers to enable 3D can install them, and then login in the standard desktop.

---

### Post by kansasnoob on 2010-12-02
> I would prefer it default to the Classic Desktop

+1! At least for now :)

---

### Post by Starks on 2010-12-02
This issue was brought up in the Ubuntu-X mailing list the other day.

> On Thu, Dec 02, 2010 at 04:26:43PM +1100, Christopher James Halse Rogers wrote:
> > Currently, because we don't ship the nouveau 3D component by default,
> > users of nVidia hardware will get the classic GNOME 2D experience on
> > Natty LiveCDs.  Worse, it's difficult to enable the binary drivers on
> > the LiveCD.
> > 
> > What opinions or prior investigations do people hold?  Is this
> > reasonable?
Well, as we've been given the direction that we're moving towards a
wayland-ish future where KMS will be a hard requirement, then as long as
we do not see plans made public for adding KMS support to the binary
drivers, it seems that investments into infrastructure around binary
drivers is going to have a limited payoff.

On the other hand, time invested in nouveau 3d support would pay off
long into the future.

> > I think that shipping nouveau 3D is probably reasonable, but something
> > we should happily back out if it turns out there are significant
> > problems.
I agree, although often it's hard for us to tell that the problems are
significant enough to warrant reverting it, especially after we've spent
all the time getting it all *in*.  :-)  There's a strong desire to push
on.

A complication is that our developers by and large have learned to stick
with -intel, especially during the development period, so we tend to get
limited testing feedback on drivers for NVIDIA hardware.

And a further complication is that the types of bugs we'd expect to see
would cause the LiveCD to fail to boot.  Even if we could get patches
for the issues, we wouldn't be able to SRU them.  (Well, we could, but
it'd be closing the barn door after the horse escaped.)

The mitigation for this is to maybe do organized testing like we've done
with mesa in the past, and have a measurable criteria that determines
go/no-go rather than using gut feel.

Probably also ensuring the failure mode is gentle and that the user is
able to switch from using 3d to 2d reasonably easily.  (Will failsafe-X
work in this situation?)

Bryce


---

### Post by kyleabaker on 2010-12-02
[QUOTE=cariboo907]Just to let you know, you can still use free software only and have 3D by installing libgl1-mesa-dri-experimental, it's in the repositories.[/QUOTE]I installed the restricted drivers, but upon reboot my screen was blank. I rebooted into recovery mode and restored graphics settings to default then used:
```
sudo apt-get install libgl1-mesa-dri-experimental
```...then rebooted again, but I still get the prompt about 3d support. How can I tell if the mesa driver is being used or setup correctly? Currently it just boots up and prompts me about 3d support then appears to load the classic gnome setup.

Thanks in advanced!

---

### Post by kyleabaker on 2010-12-03
I finally got Unity working, but for the moment I've added a "compiz --replace" to my list of applications to startup, because it was starting the session with no panels or compiz for some reason. This starts both and seems to work well for the moment. :D

---

### Post by altonbr on 2010-12-04
Sorry, can you explain the steps to get Unity to work? Install it (instead of running a liveCD), install a driver, then run that `compiz --replace` command.

Running it on my laptop instead of through VirtualBox might be the smarter choice.

---

### Post by Penguin=) on 2010-12-04
Wobblyrob, im from hull aswell!!! im from east yorkshire, what parrt are you from?

---

### Post by kyleabaker on 2010-12-04
> **altonbr said:**
> Sorry, can you explain the steps to get Unity to work? Install it (instead of running a liveCD), install a driver, then run that `compiz --replace` command.

Running it on my laptop instead of through VirtualBox might be the smarter choice.

My steps were:
[LIST]
[*]Install it
[*]Run update manager
[*]sudo apt-get install libgl1-mesa-dri-experimental
[*]Open "System -> Preferences -> Startup Applications" and add an option with "compiz --replace"
[*]Reboot
[/LIST]

I can't guarantee that will work for you, but I didn't install the nvidia drivers since they continue to cause a blank screen on boot in my previous tests. Good luck!

---

### Post by cariboo on 2010-12-04
You shouldn't have to add compiz --replace to Startup Applications. Open a terminal and type:

```
ccsm
```

if you don't have it installed it will prompt you to install it. The command will open CompizConfig Settings Manager, scroll all the way to the bottom and make sure the Unity plugin is enabled, then log out and log back in to the Ubuntu Desktop Edition. 

The system I'm using at the moment has been running Natty since the tool chain opened up, and is pretty crufty. I found that in order to get Unity to run I had to remove ~/.config/compiz, once that was done, I haven't had any problems with Unity at startup.

---

### Post by kyleabaker on 2010-12-04
@cariboo907
It worked correctly a few times, and Unity is enabled in CCSM, but it just doesn't start anything when it auto-logs in. I always have to open a terminal and run "compiz --replace". I'm not sure what I've changed, but it just won't auto start.

I'm content with this fix for now, but I'll likely reinstall in a week or two when more updates have rolled in to see if its been corrected. ...unless I find the problem before then of course. :D

The only other problem  I see is that Compiz/Unity is always on top even with the screensaver on..
[[IMG]http://img822.imageshack.us/img822/2707/screenshot2j.png[/IMG]]("http://img822.imageshack.us/img822/3383/screenshotih.png")
..do you see this too?

---

### Post by cariboo on 2010-12-04
Are you sure you're totally up-to-date? I had the same thing before updates in the last couple of days, I'm using the main Canadian server, which is supposed to be a few minutes behind the main US server.

---

### Post by kyleabaker on 2010-12-04
I'm sure everything is up to date. I'm going to remove that startup option and reboot and see what happens. Maybe an update fixed it, but it wasn't working on its own as of yesterday. *fingers crossed*

---

### Post by peterbe on 2010-12-04
> **Wobblybob said:**
> hi, as the UK has come to a halt due to a bit of snow I thought I'd do some iso testing. 

I've chosen to start with the first case on the ISO Testing tracker [http://iso.qa.ubuntu.com/]("http://iso.qa.ubuntu.com/"), the Free Software only install. The test PC has an nVidia card so I expected a 2d desktop and got one with the following message.



Which is fine, as it's a free software install I would not have the option or want to add restricted drivers so should only have the 2d DT. The question is the message states "please reboot and select "Classic session" at startup" but How?

I have a Grub startup which shows no other option and the logon which again gives no option and when I get to the DT I get the same message. I assume that if I could login as a classic session it would remove the message. Is this a bug or a feature?

I know I can go into [System], [Administration], [Login Screen] and change [Ubuntu desktop Edition] to [Ubuntu Classic Desktop] but this is not obvious from the message box and a new user would struggle to find it.
The 'login screen' applet allows you to set the desktop for your default session. That's System>Adminstration>Login Screen. That's been bothering me all day - I just found the solution when I was checking to see if a program for setting the login background existed yet. (Like GDM2Setup)

---

### Post by cariboo on 2010-12-04
I just rebooted from testing a usb device, and got the background with no panels or Unity. Opening a terminal to start the gnome-panel, which allowed me to remove ~/.config/compiz-1 again, got me back to the Unity desktop.

---

