---
title: "cant get above 800x600 nvidia geoforce 7200gs"
date: 2010-01-10
forum: Multimedia Software
---

### Post by trichotil on 2010-01-10
hi total noob here. i'm running hardy with geforce 7200gs hooked up to panasonic tc-l32c12. nvidia drivers only allow 640x480, xorg file is blank, resolution changer doesn't work at all, preferences-> screen only offers 800x600 max, and of course this lcd tv model #
is not an option in gtk. i actually lost the whole gui since i routinely skip file check (lesson learned there) but got it back by editing the unmounted partition  at which point xorg file got blanked out. tried to install nouveau  as well but no luck, the learning curve there is too steep atm for my noobiness.
things were working ok with my old monitor, an acer 23 inch. the panasonic display works fine with a different hard drive with hardy on it but migrating to it would be a huge hassle (probably where things are headed though). i guess i'm lucky it works at all, it's just irritating that the bottom of some program windows get chopped off rendering them useless.  any ideas? it was quite shocking for me to notice how many people have this problem
with tons of different fixes that help some but leave others in the dark. anyone got an xorg file i could paste in or other thoughts?

---

### Post by trichotil on 2010-01-10
i also tried envy and was able to get to the nvidia settings screen but any time i clicked on anything it went squirrely and jumped to a different part of the screen, the proprietary
drivers screen does the same thing making it impossible to change any settings. 
guess it's time to think about abandoning this installation.

---

### Post by ububaba on 2010-01-10
> **trichotil said:**
> i also tried envy and was able to get to the nvidia settings screen but any time i clicked on anything it went squirrely and jumped to a different part of the screen, the proprietary
drivers screen does the same thing making it impossible to change any settings. 
guess it's time to think about abandoning this installation.

Perhaps an improved driver can help. You can find them here.

[http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run&lang=uk&type=GeForce](http://www.nvidia.co.uk/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run&lang=uk&type=GeForce)

---

### Post by trichotil on 2010-01-10
no dice, and  right clicking and save as doesnt work either:

 If you were trying to download this file through a web browser, and
# instead are seeing this, please click your browser's back button,
# left click on the link, and select "Save as..." (or do whatever is
# appropriate for your web browser to download a file, rather than view
# it).

i'm sure there must be some way to save the code and run it but it seems
rather primitive. when folks go to the trouble to come up with nouveau you really gotta wonder about nvidia. is microsoft bribing them?
view the page yourself and watch your cpu go through the roof, how nice.
[http://uk.download.nvidia.com/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run](http://uk.download.nvidia.com/XFree86/Linux-x86/190.53/NVIDIA-Linux-x86-190.53-pkg1.run)

---

### Post by trichotil on 2010-01-10
lol just rebooted into a max 640x480 mode
so i'm really back in the stone age now.

---

### Post by trichotil on 2010-01-10
hmmm solved the problem by pasting in some generic xorg blab
(thx st3althpsycho!) into the blank one.
then opened it again and xorg.conf recommended: 
If you have edited this file but would like it to be automatically updated
again, run the following command:
sudo dpkg-reconfigure -phigh xserver-xorg

so ran it et voila! finally! after days of hair pulling!

i think the partition editor i ran added some new things
b/c i don't remember that being there before. i used a newer version than hardy on live disc to do that  with gparted. 


edit: looks like gparted updated the kernel too.
got this nasty message when i went to start virtualbox.:
> VBox status code: -**1908** (**VERR_VM_DRIVER_NOT_INSTALLED**).
had to get the new kernel# (2.6.24-26-386) from system monitor and look
in synaptic to install the right modules for virtualbox
and trash the old ones. works great now.
i guess i'll always feel like a noob when it comes to this stuff.
at least the latest crash course is over (for now at least).
hope this helps someone someday.

edit to add:
YOU GUYS AT NVIDIA CAN BLOW ME!!!:lol:

---

### Post by ububaba on 2010-01-10
Good on you!

---

### Post by trichotil on 2010-01-10
edit: hmm yes in retrospect it seems like a cool idea to make a disc of the latest version
and boot from it to run gparted to edit your partition. kind of like an upgrade w/o the inevitable hassles. 
i'm guessing this little trick would solve a zillion linux problems!
just be sure to check synaptic like i said for vbox above if you have kernel update related probs.
why does a noob like me have to figure it out this way????

---

### Post by trichotil on 2010-01-10
the home theater is back!!!
[img]http://i282.photobucket.com/albums/kk257/trichotil/v.jpg[/img]

---

