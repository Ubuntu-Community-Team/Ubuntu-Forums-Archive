---
title: "Pernemnt Mount to Windows Shares."
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by Jynks on 2010-11-17
Hi there,...

I am new to xubuntu and would like to have a "network browser" type thing like I am used to on windows. i am sure this can be done but I can not seam to get it to work.

At the moment I login to any of my windows shares using Gigolo... i simply click the connect to server button and then fill in the details. Unfortunately it asks me to do this EVERY time I wish to connect to a share. As in the icons and passwords do not save or w/e, so every time i want to connect to my windows systems I need to hit teh connect button and fill in all the derails.... 

I do not need the network shares from windows to be MOUNTED every time I boot, though if that is the way to go then cool. What I would like is a icon or something like how Gigolo works, but the icon is permanent and stores my details and password and user and everything, so I can simply click on the icon and acess the share....

I hope that makes sense...

Any help would be appreciated.

---

### Post by e79 on 2010-11-17
The easiest way would be to click on :
[B]
Places --> Connect to Server[/B]   (on the top panel)

and fill the information from your Windows share, and check the 'Add Bookmark' box. Once connected, it will create a Bookmark of the shared folder under '**Places**'

Refer to the screen-shot for examples only.

Hope this helps

---

### Post by Morbius1 on 2010-11-17
> At the moment I login to any of my windows shares using Gigolo... i  simply click the connect to server button and then fill in the details.  Unfortunately it asks me to do this EVERY time I wish to connect to a  share. I think you are missing one of the advantages of using gigolo.

When you first bring it up make a change in the preferences:
[B]Edit > Preferences > Interface>
[/B]**Select "Start minimized in the Notification Area"**
**Disable "Show auto-connect error messages"**

Then you browse to the share using the Network Tab.
Then you bookmark the share by right clicking the share icon within gigolo and select **"Create Bookmark"**
When you bookmark it select the **"Auto-connect"** option

Then have gigolo start at login:
**System > Preferences > StartUp Applications > Add > Command = gigolo**

When you login it will automatically mount remote shares and you will see an icon on your desktop. Even if you don't want to automount simply right click the gigolo icon on the panel > Bookmarks and your shares will be available to mount. Gigolo can even save the username and password if the share requires authentication.
[COLOR=Blue]
EDIT: Sorry the "Network Tab" isn't there by default:[/COLOR]
[B]Edit > Preferences > Interface>
Select "Show Side Panel"[/B]

---

### Post by Jynks on 2010-11-17
ok that all seams cool... but I do not have **system/startup applications**.

How do I add a app t startup in xubuntu?

---

### Post by Morbius1 on 2010-11-17
Isn't there a Settings > Session and Startup in the Menu?

I'm doing this from memory so ....

---

### Post by Jynks on 2010-11-17
> **Morbius1 said:**
> Isn't there a Settings > Session and Startup in the Menu?

I'm doing this from memory so ....

sorry... no there is no option like that in system..... :( 

i would printscreen but that dosn't seam to work either (on laptop with a "function" button in addition to crt+alt+shift to access print screen i think i need to get that recognized 1st

<---- EDIT

Found it!

**applications/settings/xfce 4 settings manager/session and startup**

but it asks for a command line... what is the command i need to type in to launch this gigolo?

---

### Post by Morbius1 on 2010-11-17
[COLOR=Blue]**EDIT: just type in gigolo**[/COLOR]


Do you have a /home/username/.config/autostart folder?

If not create one.

Then copy: /usr/share/applications/Gigolo
To:
/home/username/.config/autostart

I have Mint XFCE on another system. I didn't realize it was that different from Xubuntu.

---

### Post by Jynks on 2010-11-17
**/home/username/.config/autostart**

I think i have it added though the setting thing i said b4.. unfortunately I can not reboot to test right now, as I am processing a data structure and do not want to start again.... I'll reboot soon.. 

Thanks for the help... I'll post back of this works...

---

