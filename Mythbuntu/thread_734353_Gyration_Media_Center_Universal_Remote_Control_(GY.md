---
title: "Gyration Media Center Universal Remote Control (GYR3101CA)"
date: 2008-03-24
forum: Mythbuntu
---

### Post by DemonBob on 2008-03-24
[B]Difficulty: (Beginner, Intermediate, Advanced) 
Mythbuntu Release: (10.04) 
MythTV Release: (0.23 <) 
Author: DemonBob
Last Updated: Aug. 26th, 2010[/B]

This is a How To on getting the Gyration Media Center Remote working in Ubuntu 10.04. I have had this remote since 2007, and fell in love with it. The remote is a gyro mouse and media center remote all in one. In order to get this working you have to use a program called Evrouter. 

Orginal Information for getting this remote to work was gathered in this thread. [http://ubuntuforums.org/showthread.php?t=479897](http://ubuntuforums.org/showthread.php?t=479897)

Write Up:

Open up a terminal window.  

Download EVRouter for your architecture: 

i386

```
cd ~
wget http://debian.bedroomlan.org/debian/pool/main/e/evrouter/evrouter_0.4_i386.deb
```

amd64

```
cd ~
wget http://debian.bedroomlan.org/debian/pool/main/e/evrouter/evrouter_0.4_amd64.deb
```

Install EVRouter: 

i386

```
sudo dpkg -i evrouter_0.4_i386.deb
```

amd64

```
sudo dpkg -i evrouter_0.4_amd64.deb
```

Create Configuration file:

```
cd ~
touch .evrouterrc
nano .evrouterrc
```

Paste the below text. 

```
#  	Stop
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/166 "fill this in!"
	
# 	Record
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/167 "XKey/R"

# 	Pause
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/167 "XKey/P"

# 	Play
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/207 "XKey/P"

# 	Rewind
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/168 "XKey/Left"

# 	Fast Forward
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/208 "XKey/Right"

# 	Skip Back
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/165 "XKey/Home"

# 	Skip Forward
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/163 "XKey/End"

# 	Guide 
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/362 "XKey/M"

# 	Up
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/103 "fill this in!"

# 	Left
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/105 "fill this in!"

# 	Right
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/106 "fill this in!"

# 	Down
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/108 "fill this in!"

# 	Back
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/158 "fill this in!"

# 	Info
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/130 "XKey/I"

# 	OK/Enter
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/28 "fill this in!"

# 	Volume Up
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/115 "XKey/F11"

# 	Volume Down
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/114 "XKey/F10"

# 	Channel Up
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/402 "XKey/Up"

# 	Channel Down
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/403 "XKey/Down"

# 	Mute
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/113 "XKey/F9"

# 	1
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/2 "fill this in!"
# 
# 	2
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/3 "fill this in!"
# 
# 	3
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/4 "fill this in!"
# 
# 	4
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/5 "fill this in!"
# 
# 	5
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/6 "fill this in!"
# 
# 	6
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/7 "fill this in!"
# 
# 	7
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/8 "fill this in!"
# 
# 	8
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/9 "fill this in!"
# 
# 	9
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/10 "fill this in!"
# 
# 	0
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/11 "fill this in!"
# 
# 	*
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/42 "fill this in!"
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/9 "fill this in!"
# 
# 	#
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/42 "fill this in!"
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/4 "fill this in!"

# 	Clear
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd" none key/1 "fill this in!"
# 
# 	Left Click
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/272 "fill this in!"
# 
# 	Right Click
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/273 "fill this in!"

# 	Live TV
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/377 "XKey/C"

# 	Windows
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/102 "XKey/Alt_L+Control_L+BackSpace"

# 	Pictures
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/226 "fill this in!"
# 
# 	Music
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/391 "fill this in!"
# 
# 	Video
# "Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/393 "fill this in!"

# 	DVD Menu
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/410 "XKey/O"


```

Create start file. 

```
cd /usr/local/bin
sudo touch evrouter_start.sh
sudo nano evrouter_start.sh
sudo chmod 4777 evrouter_start.sh
```

Paste the below into the file. 

```

xhost +local:root
killall evrouter
rm /tmp/.evrouter* #removes a previous lock file
/usr/bin/evrouter /dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse /dev/input/by-id/usb-Gyration_Gyr
ation_RF_Technology_Receiver-event-kbd &

```

Create autostart file.

```
cd ~
cd .config/autostart
touch evrouter.desktop
nano evrouter.desktop
chmod 4777 evrouter.desktop
```

Paste the below text. 

```
[Desktop Entry]
Name=Evrouter
Comment=
GenericName=Evrouter Process
Exec=/usr/local/bin/evrouter_start.sh
Type=Application
Encoding=UTF-8
Icon=
Categories=GNOME;Application;AudioVideo;Audio;Video
X-AppInstall-Package=Evrouter

```

Get event ID: 

Run

```
ls -l /dev/input/by-id/

```

Above command should return information like below.

```
demonbob@sys-mythtv:/etc/udev/rules.d$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 2010-08-25 23:44 usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd -> ../event3
lrwxrwxrwx 1 root root 9 2010-08-25 23:44 usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2010-08-25 23:44 usb-Gyration_Gyration_RF_Technology_Receiver-mouse -> ../mouse1

```

Write down the event# associate with usb-Gyration_Gyration_RF_Technology_Receiver-event-kbd and usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse. In my case this is 3 and 4.

Create udev rules file. 

```
cd /etc/udev/rules.d
sudo touch 10-local.rules
sudo nano 10-local.rules
```

Paste the below into terminal. Replace the event[**#,#**] with your corresponding numbers. Change the owner to the your user account

```
KERNEL=="event[3,4]", OWNER="YOUR_USERNAME"

```

Reboot

**===Extras===**

**Jump Points:**

**Custom Scripts:**

[COLOR="Red"]MythFrontend Close and Stop when green MCE button is pressed.[/COLOR]

I wrote a script to make the Green MCE button to start and stop mythfrontend

1. Download the attachement labeled mce.start.sh

2. copy the file to /usr/local/bin/

3. Change the premissions of the file to executable.

```
sudo chmod 4755 /usr/local/bin/mce.start.sh
```

4. Edit your .evrouterrc for key event 102 and make it look like so. (Notice the change at the end)

```
"Gyration Gyration RF Technology Receiver" "/dev/input/by-id/usb-Gyration_Gyration_RF_Technology_Receiver-event-mouse" none key/102 "Shell/mce.start.sh &"
```

[COLOR="red"]Mythfrontend swith to boxee[/COLOR]

This is a simple replacement for the above script for if you have multiple media clients installed you can switch between them. In the code below i use boxee, but it can be modified for any combinations of applications.

```
if [ "$(pidof mythfrontend.real)" ] && [ "$(pidof Boxee)" ]
then
	killall mythfrontend.real
	killall Boxee
	
	
elif [ "$(pidof mythfrontend.real)" ]
then
	killall mythfrontend.real
	exec /opt/boxee/run-boxee-desktop

elif [ "$(pidof Boxee)" ]
then

	killall Boxee
else

	exec mythfrontend

fi
```

---

### Post by volkswagner on 2008-03-24
I have this same remote, two in fact.  Unfortunately this fix requires Evrouter.  At this time there is no Evrouter AMD64 version available.  I was hoping for a more universal solution.  I thought Gizmod or Gizmo Deamon would be an alternative for the AMD64 dilemma.  I think the remote would need native support in Gizmod so no joy there either.

Can you post your config file for Evrouter.  I was not able to get any of the jumpoints to work.  I would like on of the button to control the card and or input.  Although now with .21 this is avail in the menu when pressing "M" which is mapped the the guide button on this remote.

Check out my post at the inactive forum for gizmod.  It looked so promising since it captured all buttons that work with the RF.

[http://sourceforge.net/forum/forum.php?thread_id=1950180&forum_id=467994]("http://sourceforge.net/forum/forum.php?thread_id=1950180&forum_id=467994")

I am happy to help.  PM me if you wish.

Cheers

PS: Doesn't LIRC have support for the ATI RF remote?

---

### Post by napsilan on 2008-03-24
can you --force-architecture the evrouter deb?  

I'm also rather surprised/pleased that my thread of talking to myself was useful to someone

---

### Post by superm1 on 2008-03-25
Is evrouter open source?  We can plan to get it into Interpid at least :)

---

### Post by DemonBob on 2008-03-25
I tried contacting the author, the email bounces back. I'll try other avanue's of contact in the morning. The source does not appear to be avalible.

EDIT. NVM Source is avalible [http://www.bedroomlan.org/~alexios/files/SOFTWARE/evrouter/evrouter_0.3.3.tar.gz](http://www.bedroomlan.org/~alexios/files/SOFTWARE/evrouter/evrouter_0.3.3.tar.gz) 

Stright from the authors site: "The tool is available as source, Debian and RPM packages. It's provided under the terms of the GNU General Public License, version 2. "

If someone can take a look at it and see what needs to be done to accomdate 64 bit proc

---

### Post by DemonBob on 2008-03-25
> **superm1 said:**
> Is evrouter open source?  We can plan to get it into Interpid at least :)

I'd love to help get it included. 

Basically to get the gyration remote working. All it needs is evrouter package and a packges for the few config files. 

/usr/local/bin/evrouter_start.sh
/usr/local/bin/mce.start.sh (short code i wrote to map to the Green MCE button, open's and closes mythfrontend)
/home/username/.config/autostart/evrouter.desktop (Autostart entry)
/etc/udev/rules.d/10-local.rules (to give the current user premission over the dev entry)
/home/username/.evrouterrc <-- config file will keymappings and jumppoint mappings. 

and sql file and script to insert predefined jumppoints keymaps (Alt+ctrl+1 etc) in the the mythtv database.

All the information is already here, except for a predefined keymapping, atnd jumppoints everyone can agree on. Something useable for new user's on thier first install, that they can modify later.

Hell i might even give a try at coding a gui tool, where users can configure the remote keymappings, and jumppoints. If we can get it included.

---

### Post by volkswagner on 2008-03-25
> can you --force-architecture the evrouter deb? 

I am not sure what this means.  It does sound scary.  I will be willing to try once I create an image of my stable system for easy backup/restore.  I should have done this by now, this week it shall happen

> 
/usr/local/bin/mce.start.sh (short code i wrote to map to the Green MCE button, open's and closes mythfrontend)

I would be interested in this, if you can post this.  
> 
/home/username/.evrouterrc <-- config file will keymappings and jumppoint mappings

I tried to edit my rc file.  I tried to map "Y" to several unused buttons like, TV and Video buttons.  This would not work.  I was successful in my edit of "esc" to the back button.

Here is my rc file, thanks to napsilan for posting his.  Any suggestions how I can map the "y" key?

---

### Post by DemonBob on 2008-03-25
Which key are you trying to map Y to specificually? and what is the funtion of Y?

---

### Post by volkswagner on 2008-03-25
Selecting "Y" while viewing live tv in mythtv, will change the tuner to the next available tuner.  This can be accomplished by selecting menu ("m") which is already mapped to the guide button.  This makes a direct short cut, rather than via the OSD menu.

I have tried to use the video key and the tv key to no avial.

---

### Post by napsilan on 2008-03-25
@volkswagner

using dpkg --force-architecture will cause dpkg to install 32 bit debs onto a 64 bit system.  I've used it with wine debs before without any problems, but I have not tried it with evrouter.

---

### Post by lifecomm on 2008-07-16
> **DemonBob said:**
> I'd love to help get it included. 

Basically to get the gyration remote working. All it needs is evrouter package and a packges for the few config files. 

/usr/local/bin/evrouter_start.sh
/usr/local/bin/mce.start.sh (short code i wrote to map to the Green MCE button, open's and closes mythfrontend)
/home/username/.config/autostart/evrouter.desktop (Autostart entry)
/etc/udev/rules.d/10-local.rules (to give the current user premission over the dev entry)
/home/username/.evrouterrc <-- config file will keymappings and jumppoint mappings. 

and sql file and script to insert predefined jumppoints keymaps (Alt+ctrl+1 etc) in the the mythtv database.

All the information is already here, except for a predefined keymapping, atnd jumppoints everyone can agree on. Something useable for new user's on thier first install, that they can modify later.

Hell i might even give a try at coding a gui tool, where users can configure the remote keymappings, and jumppoints. If we can get it included.

Hi DemonBob, et al.

I saw the above message.

I really need help getting Mythbuntu and Gyration working together - but I am a complete idiot and am way over my head! Could you please help me to better understand your instructions?  I've never used Linux before - ever!   However, I do have a very good Linux friend (who's very busy) that will help me.  But I hate for him to spend the time researching and working out a solution.

BTW:  I have the GYR3101US remote

Thanks in advance,
Tom

---

### Post by pennstatebadboy on 2008-08-03
Does anyone know where I can find a list of XKey commands?

Specifically, I'm trying to change the up and down channel buttons on my Gyration remote control from mimicking the up and down keyboard arrow keys to mimicking the page up and page down keys. Right now, my evrouter_gyration.txt file reads "XKey/Up" "XKey/Down" for up and down, respectively.

What is the command for Page up and Page Down? I would think it would be something such as "XKey/PageUp," but that doesn't work. Anyone know?

---

### Post by volkswagner on 2008-08-03
Did you try PgUp and PgDn?

---

### Post by pennstatebadboy on 2008-08-03
Yes. And I get the following error when I run evrouter:

stdin:56: invalid or unknown keysym name "PgUp".

Any ideas?

---

### Post by volkswagner on 2008-08-03
Wish I could be more help.  I love this remote.  On mythtv site Keybinding is listed as "Page Up".  I thought I could run Gizmod in debug mode to see how my keyboard is reading the key.  It showed up as PAGEUP.  If you have not tried the following, please list what does not work.

Page Up
Page_Up
PAGEUP
PAGE UP
PAGE_UP
??????????

This MRS. is sleeping in the bedroom with my frontend using Gyration.

Otherwise I would try on my setup.  

I am not sure what program would record the key event for you, perhaps a keylogging app.

---

### Post by pennstatebadboy on 2008-08-03
"This MRS. is sleeping in the bedroom with my frontend using Gyration."
Dude. That sounds so dirty. Lol.

I'll try those options out. Thanks.

---

### Post by pennstatebadboy on 2008-08-04
None of those options work. Any other ideas?

---

### Post by pennstatebadboy on 2008-08-04
Hold it! Page_Up and Page_Down work. Thank you so much.

If only the pictures, tv, and videos buttons worked.

---

### Post by Disparu on 2008-09-06
I got the remote working using the instructions in the very first post. This has me excited since it is an awesome remote. 

I have a few issues I still need help with though.

A few of the jump points don't generate any kind of output even when though they are mapped.

The gyro mouse feature of the remote stopped working once I set up evrouter and only the buttons work now.

---

### Post by volkswagner on 2008-09-06
Did you set up udev rules.  The remote is divided into three parts.  I cant remember my settings, I will post tomorrow.

Anyway you need to make sure you have permission to use all three.  I don't think the mouse is an issue but the other two are.

Keyboard
mouse event.

I believe the mouse event include the four shortcut buttons.

EDIT:  You can verify it is a permission issue by chmod or rt click and change permissions.  Problem is reverting back upon a reboot.  >device>input>......

---

### Post by Disparu on 2008-09-07
Well I know the gyro mouse function works by default when plugged into ubuntu and it did work previously, I tested on my laptop with the same results. I am guessing the gyro function is physically broken. The mouse left and right click work fine, but the green light on the receiver does not light up when i hold down the gyro button.

---

### Post by volkswagner on 2008-09-07
That's to bad.  One thing about the Gyro function, it does not seem very tough.  One of my remotes has fallen of the bed several time.  Now it starts a high pitched squeal on its own.  The  mouse now is erratic.

---

### Post by mrand on 2008-09-08
I started collecting info on the Gyration based remotes at
[http://www.mythtv.org/wiki/index.php/Gyration-based_MCE_Remotes](http://www.mythtv.org/wiki/index.php/Gyration-based_MCE_Remotes)

Please add and/or correct anything there.  I haven't played with evrouter or xbind, so those sections are blank.  

For those that are wondering, it is possible to use LIRC with these guys.  The above wiki page has info on it, and a preliminary lircd.conf 

Also, I believe the kernel patch related to the non-functioning keys (mention here [http://ubuntuforums.org/showthread.php?t=479897&page=2#19](http://ubuntuforums.org/showthread.php?t=479897&page=2#19)) should be integrated into 2.6.27, which Intrepid (8.10) is to be based upon.

[INDENT]Marc[/INDENT]

---

### Post by DemonBob on 2010-08-26
Just to let everyone know. I updated my system to 10.04 and decided to get my remote working on it, I upgraded from 8.04. So i decided to update my original post and turn it into a how to.

---

