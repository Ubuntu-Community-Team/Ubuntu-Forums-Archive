---
title: "Random Wireless Dropping on WPA2-PEAP network"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by Piro24 on 2012-09-15
So, I've got a weird problem with the wireless on my Thinkpad T430.

I'm connecting to a network secured with WPA2-PEAP, generally, it connects at first, then drops the connection within a minute or two. Then, it will try to reconnect, and generally is unsucessful. 

Killing NetworkManager and letting it reconnect fixes the problem... sometimes. 

The past two days, I've had to do that, and the connection "just stuck" after that. Now, it seems to be going in an unfortunate loop of re-connecting and then dropping the connection. 

Not sure how to go about this... I'm using the iwlwifi driver that was enabled by default on the install.

Any suggestions would be helpful. Thanks.

---

### Post by varunendra on 2012-09-16
Usually we ask for some common command outputs to start troubleshooting in wireless problems. Almost all of such commands have been included in a nice script created by one of our dedicated members- *anewguy*.

Download this script (created by anewguy and tested by some experts here) :
[http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) (1.8kB)
and run it to create a "netinfo.txt" named file that will hold almost all the info we initially need to start troubleshooting.

**Terminal (commandline) method to download and run the script (short & easier):**
(simply copy-paste-'Enter' the following command into a terminal):
```
wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
```
After entering the above command, just enter your password in the terminal when prompted for. A "netinfo.txt" file would be automatically created in your home directory (along with the just downloaded "wireless_script"). Attach this file in your next post.

**GUI method to download, run, and post back results :**

[LIST=1]
[*]Right-click > save the link to download the script.
[*]Right-click the downloaded file and go to "Permissions" tab. There, tick the "Execute" checkbox to make it executable.
[*]Now double-click the file and select "Run" in the opened dialogue box. Provide your password when asked.
[*]A fresh new file named "netinfo.txt" will be created in the same directory. Just attach it in your next post. *(Note that it may contain your **WAN IP** in some cases like a ppp connection. So if you consider it confidential (although it is not), simply delete or replace it before attaching the file)*
[/LIST]

---

