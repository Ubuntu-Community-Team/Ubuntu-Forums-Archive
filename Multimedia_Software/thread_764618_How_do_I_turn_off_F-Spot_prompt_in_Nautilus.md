---
title: "How do I turn off F-Spot prompt in Nautilus"
date: 2008-04-24
forum: Multimedia Software
---

### Post by Stochastic on 2008-04-24
So I've got the release candidate of UbuntuStudio Hardy up and running, but there's one thing that keeps bugging me.  Every time I open a folder (sometimes even a folder on a partition) that has digital photos I get a bright blue notification that there appears to be digital photos on this device and that I should open F-Spot (even if F-Spot is already open).  How do I make this notification go away?  Am I the only one who finds this extremely annoying?

---

### Post by Stochastic on 2008-04-24
Bump.  Am I the only one who has this problem?

---

### Post by Stochastic on 2008-04-28
Bumpity, bump, bump.

---

### Post by r.stiltskin on 2008-06-08
Open Nautilus, go to edit/preferences/media, then on the "Photos" line change the selection to "Do Nothing".

---

### Post by Stochastic on 2008-06-09
Sorry mate, already tried that, but still the notification is there.

---

### Post by gandaran on 2008-06-09
system » preferences » devices and media » cameras, un-tick the box import photos.

---

### Post by Stochastic on 2008-06-11
> **gandaran said:**
> system » preferences » devices and media » cameras, un-tick the box import photos.

I'm looking in system >> preferences and there is no 'devices and media' section.  I even checked in the Main Menu Editor and no options were hidden.  It's also not in the Control Center, or the Administration menu.  I'm on 8.04.

Edit: I just found it, it's called Removeable Drives and Media, but my "import photos" box is not ticked.

Edit #2: A bit more clarification on the issue, I'm mainly receiving this prompt when browsing my Fat32 partition, even if the folder on that partition doesn't have any digital photos - this leads me to wonder if there's something wrong in my /etc/fstab that's making nautilus do this.  I also see the prompt when I attach a digital camera or memory card with photos (that part I'm not too concerned with, though I never use F-spot, so turning the prompt off completely would be fine by me).  Here's a picture of the offending message: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=67153&d=1209143042[/IMG]

---

### Post by larstorben on 2008-07-11
I also hate this thing. It's wasting space and just plain pointless.

I know the media has photos on it, for crying out loud--that's why I'm browsing it.

Also, the wording is just annoying. "This media contains digital photos". Well, what kind of photos were they expecting? It's a computer.

Neither of the above would bug me (and I would not feel inclined to rant about them) if only there was the option to turn this useless feature off. Let people who want it use it. I hate it and it's in my way.

---

### Post by melenor on 2008-11-30
I can not find the place to turn this off in 8.10 any help would be nice. Thanks

---

### Post by melenor on 2008-11-30
bump

---

### Post by melenor on 2008-12-07
bump

---

### Post by mc4man on 2008-12-07
For 8.10
If the prompt is from inserting a digital camera then go to file management -> media -> photos and set to 'do nothing'
(home -> edit -> preferences -> media or edit menus -> preferences and enable 'file management'

If the prompt is caused by some other action, post what it is.

Edit: if it happens to be a usb drive than the 'do nothing' should also take affect.

Otherwise move your photos out of the root of the drive, ie. put in a folder or rename the folder they're in.
Certain names of folders will trigger the event. For instance a folder named DCIM with anything inside will cause the 'autorun', may be others.

Actually somewhat interesting - another way to run a script off of connecting a usb drive

---

### Post by melenor on 2008-12-08
I have tried all of that if there is a folder or a picture in the root of the drive it gives off that prompt. one example is a flash drive with only documents on it, but it has a folder named school so it gives me that prompt. The most annoying is on my internal drive, it has pictures but i don't want to delete those pictures. It has no autorun sort of thing. I have made all the different effects into do nothing.

---

### Post by melenor on 2008-12-20
Bump. 
This is extremly annoying because this is on my NTFS drive that i use quite regularly, because i have to boot into both, and i need the information on both OSes.
Thanks.

---

### Post by r.stiltskin on 2008-12-20
In Nautilus, if you click edit/preferences, does that not open a "File Management Preferences" box with a tab marked "Media"?

(and a checkbox marked "Never prompt or start programs on media insertion")?

Have you checked that box?

---

### Post by melenor on 2008-12-20
i have clicked that, i clicked the "Never prompt or start programs on media insertion"
Nothing seems to work, I hate the prompts that appear on the drives.

---

### Post by r.stiltskin on 2008-12-20
Sorry, I misunderstood.  I thought you meant a prompt that pops up on your screen when you plug in the drive.

If you want to get rid of the fspot bar (with button) that appears **in Nautilus** under the location bar (or menu bar), you can get rid of that by uninstalling fspot.

My guess is that there is something hard-coded into Nautilus that looks to see if fspot is installed and if it is, it invokes that prompt (but I could be wrong).

---

### Post by melenor on 2008-12-20
after uninstalling F Spot it wants me open Brasero Disc Burning.
I think the problem is that ubuntu sees the NTFS drive as a Picture CD, and not as a Hard Drive.

---

### Post by melenor on 2008-12-20
i took a look at my fstab to see if i found something that would tell me why it thought that the NTFS drive was a picture CD, this is the line
```
/dev/sdb2	/media/Data	ntfs-3g	uid=1002 0 0
```
Thanks for any help.

---

### Post by r.stiltskin on 2008-12-21
There's nothing there that says "picture cd".  What if you uninstall brasero?  (I like k3b anyway.)

---

### Post by mc4man on 2008-12-21
This is starting to seem like your knocking down the house to fix a sticky door.

As far as volumes on internal drives, I can't see that any auto action would be initialized when mounting so I'm gathering your talking about a 'prompt bar' when the volume is opened in nautilus.

Maybe just post a screenshot (use alt+PrtScr on a medium sized window.

---

### Post by r.stiltskin on 2008-12-21
Yes. Prompt bar is exactly what I would call it.  See Post #3.

You'd think that the view menu would allow it to be de-selected, but there is no such option as far as I can see.

---

### Post by melenor on 2008-12-24
here is a pic of it. but it does say the burning thing, not the F-spot.

If this is not able to be changed in 8.10 how do i make submit it so that it can be changed for 9.04?

---

### Post by mc4man on 2008-12-24
I can only duplicate this when there is a folder named Pictures with a .jpeg inside on an ntfs volume in 8.10 (8.04 doesn't 'see' picture cd

If I put the Picture folder inside of another folder (tried 'School') it doesn't show up.
The prompt is determined when the volume is mounted, any changes, ie. renaming Pictures, isn't reflected till the volume is unmounted and remounted. In other words if I delete 'Pictures', close and reopen the folder, the prompt remains.

---

### Post by jfd5xte on 2009-06-11
Anybody know if this is fixed in Jaunty?

---

### Post by Xanfer on 2009-08-11
2 jfd5xte
No, it haven't been fixed yet...

---

### Post by dtach on 2011-07-03
bump. it's now 11.04 and I'm still dealing with this BS. it only happens on external drives.

---

