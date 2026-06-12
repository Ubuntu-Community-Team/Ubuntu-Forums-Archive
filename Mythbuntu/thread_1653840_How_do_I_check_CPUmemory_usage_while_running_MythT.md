---
title: "How do I check CPU/memory usage while running MythTV?"
date: 2010-12-27
forum: Mythbuntu
---

### Post by dtaylorl on 2010-12-27
I'm wondering just what the title asks. Video playback drops frames from time to time and I want to test to see if its because my hardware is underpowered.  I would also like to test my CPU load while during HD playback.

---

### Post by 4dognight on 2010-12-27
You can run 'vmstat 2'
or
'top'

in a terminal.

I prefer vmstat. It will show you all that you ask and more.

---

### Post by LowSky on 2010-12-27
I like running htop (you need to install it first)

its a bit better than regular top

---

### Post by dtaylorl on 2010-12-27
Ok, thanks.  I'll give those a try.  Is there a way to view the info live as MythTV is running, or do I have to exit myth and then view the output?

---

### Post by 4dognight on 2010-12-27
If your frontend is starting automatically, which is default. You can exit the frontend, open a terminal and run whichever of the 3 commands mentioned you prefer. Then start the frontend from the menu. While the frontend is then running, you can ALT-tab back to the terminal window to see what it is up to.

---

### Post by dtaylorl on 2010-12-27
Perfect, I always forget about the ALT-tab combo.  I actually ended up connecting to the machine remotely via SSH instead.  My CPU usage is fine (~30%), but it looks like I am using a fair bit of swap space to meet my memory requirements. How does vmstat report the amount of memory used?  It says my swpd is 155244.  Is that ~155MB?  I have a decent amount of RAM in the machine (1GB I think)... is it normal for MythTV to use more than that?  If so I guess I'll upgrade it.

---

### Post by 4dognight on 2010-12-27
vmstat defaults to KB, so you have 155MB swapped. If you have sufficient memory and want to prevent swapping, as linux will swap by default, even with sufficient memory. You can add vm.swappiness=0 to /etc/sysctl.conf, and reboot. This will make linux avoid swapping as much as possible. Mythtv isnt really memory hungry. Do you have anything else running on the server?
If you run top or htop, you can have it sort on mem usage to see where its being allocated.

---

### Post by dtaylorl on 2010-12-27
Because vmstat was showing more memory allocated to swap than was free I assumed that it was only using a swap because there wasn't enough space on the physical RAM (running vmstat on my laptop shows 0 for swpd).  Additionally, I assumed that the remaining "free space" was on the swap.  Now that I've run vmstat I see that this isn't the case.  I have 768MB of Ram and there are still a few MB of free space on it... but not much.  After ~5 minutes of TV playback I'm down to only 8MB of free space.  We'll see if this runs out as I continue watching.

Edit: My swap space is up to almost 2GB.  Is there any chance that this could hurt performance?

---

### Post by 4dognight on 2010-12-27
if you have swapped out 2gb, that is bad, very bad.
Can you post  your top display sorted by memory.

---

### Post by dtaylorl on 2010-12-27
I should point out that most of those 2GB aren't being used... only 169MB - the rest is free.  So I'm not sure why there is so much being allocated to swap.  mythfrontend is basically the only process using any memory or CPU.

---

### Post by 4dognight on 2010-12-27
Oh, I thought you had 2gb swapped out.
Still , try setting the vm.swappiness as i previously mentioned.

---

### Post by keepitsimpleengr on 2010-12-28
> **LowSky said:**
> I like running htop (you need to install it first)

its a bit better than regular top

Great advice!

HTOP is great for MYTHTV.  It runs in a terminal window.  I usually run it on one of the 4 desktops but you can also run it from a console (Alt-TAB-Fn).  It has a text based customizable graphical display which is good for quick glances.

You can kill programs if run as "sudo htop", and has convenient function key operations such as search, easy column sort selection and search.  You can also customize it and use colors.

---

### Post by kyphos on 2010-12-28
> **keepitsimpleengr said:**
> Great advice!

You can kill programs if run as "sudo htop", and has convenient function key operations such as search, easy column sort selection and search.  You can also customize it and use colors.

How does one go about finding "htop" and then install it on a Mythbuntu system??
(please assume minimal familiarity with Ubuntu).

Thanks.

---

### Post by 4dognight on 2010-12-29
from a terminal, type in 

sudo apt-get install htop

---

### Post by kyphos on 2010-12-29
@4dognight,
Thanks!!

---

