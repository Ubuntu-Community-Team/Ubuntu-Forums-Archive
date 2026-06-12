---
title: "Getting Wireless to load at Startup"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by flourboy on 2009-04-13
I have a Netgear WG311 (Chipset Marvell 88w8335) on my PC that i have installed Ubuntu on.  I went online to find out how to get Ubuntu to recognize the Wireless card.  I went through the guide and it recognized it perfectly.

However whenever i restart the computer, Ubuntu does not recognize the card again and i then have to use the Terminal to get it to connect.

Is there a way to get Ubuntu to load the wireless card at startup?  If so, how would i go about doing this, as i am a newbie to Ubuntu.

---

### Post by Tr10 on 2009-04-13
> **flourboy said:**
> I have a Netgear WG311 (Chipset Marvell 88w8335) on my PC that i have installed Ubuntu on.  I went online to find out how to get Ubuntu to recognize the Wireless card.  I went through the guide and it recognized it perfectly.

However whenever i restart the computer, Ubuntu does not recognize the card again and i then have to use the Terminal to get it to connect.

Is there a way to get Ubuntu to load the wireless card at startup?  If so, how would i go about doing this, as i am a newbie to Ubuntu.

I'm fairly new to ubuntu also, but my thoughts would be to create a script that runs on startup with the terminal commands in it.

Someone with more knowledge might give you a permanent solution.

---

### Post by flourboy on 2009-04-13
The Guide i used said that i could use a script to do that, but being a newbie, i have no clue how to do it.

---

### Post by Tr10 on 2009-04-13
> **flourboy said:**
> The Guide i used said that i could use a script to do that, but being a newbie, i have no clue how to do it.

Well, in ubuntu you have the terminal which you are already familar with.
You can create a shell script that will run as if you were typing in terminal.

My friend google gave me this option:
[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

This would be what you're looking for, the title of the script could be anything as long as it contains the commands you would enter into terminal.

I'm pretty sure that should fix your problem atleast for now.
Though I have never had to use a startup script like that, it seems pretty straight forward. If you have questions, feel free to ask and I will try to help you to the best of my ability, though, I am new just like you :P

---

### Post by flourboy on 2009-04-13
Thanks for the link.  Now a new problem though.  It keeps telling me that i don't have permission to save the script file to the etc/init.d/ folder.

Am i overlooking something?

---

### Post by Tr10 on 2009-04-13
> **flourboy said:**
> Thanks for the link.  Now a new problem though.  It keeps telling me that i don't have permission to save the script file to the etc/init.d/ folder.

Am i overlooking something?

In Ubuntu you have to have root access to edit that folder.

You would have to put sudo in front of the commands entered in terminal.

For more information on sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

