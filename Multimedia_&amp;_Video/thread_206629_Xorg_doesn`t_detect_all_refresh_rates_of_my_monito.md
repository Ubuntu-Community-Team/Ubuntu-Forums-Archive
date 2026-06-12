---
title: "Xorg doesn`t detect all refresh rates of my monitor"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by DjDarkman on 2006-06-30
I have a big problem ,xorg doesn`t detect all my refresh rates of my monitor ,if i run sudo dpkg-reconfigure xserver-xorg ,I can set it up manualy ,but after I set up my nvidia drivers it just replaced with the old configuration ,so here is my configuration with a working 3d accelaration ,how can I add refresh rates to my monitor?for example add 75Hz to the 1024x* resolution
if someone can help me ,please write the changes to the pastebin ,or tell me how do do it ,thank you.

[http://djdarkman.pastebin.us/827]("http://djdarkman.pastebin.us/827")

---

### Post by tseliot on 2006-06-30
Try point 5 of the Problems Section of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

If that doesn't work try point 10

---

### Post by cbeaudin on 2006-06-30
You need to edit the values of xorg.conf. I had a great tutorial and i cant find it now... but ill give you the general idea, hopefully the right way.

Please keep in mind i am new to linux, you may want to have a second opinion to tell you if these steps are right or not, i dont want to mess anything up for you.

1. Make a backup of xorg.conf. To do that you open a terminal and type:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

2. Open etc/X11/xorg.conf in gedit.

3. Look up the specs of your moniter because you have to enter it in manually.

4. You should see two spots you need to edit:
===============================================
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70   ---- This is the horisontal refresh
	VertRefresh	50-120    ---- Vertical refresh
EndSection
===============================================
Change those two ranges to what your moniter specs say.

The second section you will see something like this:
======================================================
SubSection "Display"
		Depth		24
		Modes		"1280x1024" "800x600" "640x480"
	EndSubSection
======================================================
Again, change the resolutions to reflect your moniter.

5. Save the file to your desktop.

6. Replace the existing xorg.conf with the one you have created on your desktop using a terminal.

7. Log out and hit ctrl+alt+backspace to restart xserver.

8. Log in and you should have the max resolution of your moniter by default.

If anything goes wrong use this command in the terminal at startup to replace your old xorg.conf:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by DjDarkman on 2006-06-30
Thank you ,it helped me out.

---

