---
title: "Deleting old kernels and headers"
date: 2011-12-21
forum: Mythbuntu
---

### Post by GaryP2 on 2011-12-21
[SIZE=2]Greeting – is there any risk of breaking anything by removing the old linux-image and linux-headers kernel packages using Synaptic Package Manager? I have a Mythbuntu 10.4 system upgraded to MythTV 0.24.1 that I only periodically run the Update Manager to apply security and stable updates. I have 4 or 5 old kernels and associated headers and would like to delete all but the current and one revision back. I created a relatively small root partition and it’s now over 80% full (only typically fills up more when I do these updates). [/SIZE]
 
[SIZE=2]It looks like I should be able to select the following three packages for each old kernel and select **Mark for Complete Removal**:[/SIZE]
 
[SIZE=2]**linux-headers-2.6.32-nn**[/SIZE]
**[SIZE=2]linux-headers-2.6.32-nn-generic[/SIZE]**
**[SIZE=2]linux-image-2.6.32-nn-generic[/SIZE]**
 
[SIZE=2]Everything I’ve read about Ubuntu in general suggests that Synaptic Package Manager should handle this okay and not delete anything that’s a dependency on something else, etc., but I just wanted to see if there was anything out of the ordinary for Mythbuntu or a MythTV install. [/SIZE]
 
[SIZE=2]As good as the Update Manager has gotten in keeping Ubuntu patched and current, I’m not sure why there isn’t a more automated mechanism for cleaning up stuff like this unattended. I’ve read there are other approaches including CLI, scripts, and the ubuntu-tweak GUI, but I’d like to stick with Synaptic unless there is a compelling reason to do it a different way. Thanks much.[/SIZE]

---

### Post by thatguruguy on 2011-12-21
I generally wait a week or two after installing new kernels to see if there's any breakage.  If not, I delete the old kernels.  So far, I've had no problems, although (as always) YMMV.

---

### Post by azmyth on 2011-12-21
I delete old ones after about two weeks as well and I've never had an issue. Just make sure you do uname -r first so you don't accidentally delete a kernel that you're currently running. I think it gives you a warning though if you accidentally try.

---

### Post by oldsoundguy on 2011-12-22
Ubuntu Tweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)).. nice gui that lets you manage not only the kernels, but clean out the outdated/unused material that DOES hang around in Linux (NOTHING like the garbage dump left behind in Windows!! LOL)

I keep the current and the previous two kernels .. but that is me.  Whatever floats your boat.

---

### Post by GaryP2 on 2011-12-22
[SIZE=2]Thanks for the feedback/recommendations. I successfully deleted most of the old kernels and headers on my Mythbuntu systems and everything still seems good. I also run Ubuntu under VirtualBox on a laptop and had around 15 old kernels laying around that I deleted and bought back lots of space.[/SIZE]

---

### Post by gordintoronto on 2011-12-22
You can also open a terminal and issue this command:
sudo apt-get clean

which will delete all the .deb files from system updates. You probably have at least 300 MB of these files.

---

