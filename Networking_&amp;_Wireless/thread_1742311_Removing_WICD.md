---
title: "Removing WICD"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by biomedtek on 2011-04-28
Okay, apparently there is some bug when using wicd with 11.04. I used wicd with no problems until I upgraded to 11.04. Now I do not get an indicator on the menu bar, so I can't manage my network connections, although I am connected to my wireless router. I tried removing wicd through the ubuntu software center, then rebooting and reinstalled it, still no indicator. My laptop is a HP DM3 with AMD processor that dual boots with Win7. I can't continue to use Ubuntu without the wireless indicator. Can anyone tell me how to revert to the default network manager, which I'm hoping will have a menu indicator. Otherwise it's goodbye Ubuntu and hello Win7.

---

### Post by cbowman57 on 2011-04-28
Have you already tried 'sudo apt-get purge wicd && sudo apt-get install network-manager --reinstall' ?

Not certain but that might do it.

---

### Post by biomedtek on 2011-04-28
I can try that, do I type it exactly as you have indicated, is it all one command line?

---

### Post by williejones on 2011-04-28
You can do it in 2 steps to make it easier.
1 Install network-manager, reboot and see if you can use it.
2 Remove WICD

---

### Post by biomedtek on 2011-04-28
that worked, I now have an indicator for network.
Thanks much!

---

### Post by cbowman57 on 2011-04-28
Great news.  Like willie said, you can do it in two steps, the '&&' just lets you string multiple commands together.

---

### Post by chenxiaolong on 2011-04-28
Ubuntu blocks the regular system tray icons from showing in Ubuntu 11.04. You can run this command to reenable the system tray:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Then you can use WiCD if you prefer it.

---

### Post by biomedtek on 2011-04-29
I might try this command to reenable the tray, but will that give me a tray that's cluttered with many icons? Right now I just have bluetooth, battery, network, and a couple more showing on the right side of the menu bar.

---

### Post by chenxiaolong on 2011-04-29
That command will enable all icons. By default, Ubuntu enables the list below:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray']"
```

to enable WiCD, just add it to the end of the list. I'm not sure what Wicd's name is to Ubuntu. Try this:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'wicd-client.py']"
```

---

### Post by biomedtek on 2011-04-29
Ok, when I get home from work I'll try it, or maybe I'll just enable all. I originally switched to Wicd cuz network manager kept dropping my wireless with 10.10, it was a bug. Maybe network manager will behave under 11.04 and I can just leave it as is, although Wicd does seem more robust.

---

### Post by biomedtek on 2011-04-29
bad news times 2.
I can't continue to use network manager cuz it still has that same old bug where it keeps dropping my wireless. So, reinstalled Wicd and tried your command to enable all icons, but that did not work. Then tried your command to add wicd, still no good. I'm back to using Wicd right now on a wired connection, but just can't get the icon to show with natty. Guess I'm out of luck,

---

### Post by cbowman57 on 2011-04-29
I'm at a loss as to what could be the problem on your system.  I have successfully used the network-manager, wicd & connman on Natty w/unity

Perhaps connman will work for you.

[http://ubuntuforums.org/showthread.php?p=10613656]("http://ubuntuforums.org/showthread.php?p=10613656")

---

### Post by chenxiaolong on 2011-04-29
Oh yeah...I forgot to say that you have to log and then log back in after you enable all the icons.

---

### Post by biomedtek on 2011-04-29
well I installed connman and I do have a network icon now. The thing is that the wireless behaves exactly like network manager, constantly connecting and disconnecting. Wicd was the only interface were the wireless worked properly. Guess I'll just leave things as is for now and use the laptop with a wired connection when using Ubuntu. Maybe at some point there will be an update to Wicd and I can try it again. I'm kind of bummed, I'm just a novice with linux, but did enjoy playing around with it, at least until natty came along. Kind of wish I never upgraded, things worked well with 10.10. Thank you guys for trying to help.

---

### Post by phopon on 2011-04-30
You can still use the "classic" ubuntu in 11.04. On the log-in screen at the bottom there is the option to use "ubuntu" or "ubuntu classic", just choose classic and it should look like it used to and I believe that the systray will work the way it did in 10.10

---

### Post by phopon on 2011-04-30
Also, when setting the whitelist to 'all' I had some serious problems as well. Instead of 'all', just add both 'python' and 'wicd-client.py' to the whitelist.

---

### Post by biomedtek on 2011-04-30
Redoing the white list didn't help, but I got the icon to show after some googling and further reading. Here is what I did: I logged back into ubuntu with the classic desktop and noticed that the wicd icon was still missing. I then ran wicd-client and the tray icon appeared and I was able to have access to wicd settings. I then logged out and went back into unity, and again no icon. Once again I ran wicd-cliend and it worked! Apparently with the default install, wicd-client does not run. Now all I need to do is figure out how to have the client automatically run at log in.

---

### Post by chenxiaolong on 2011-04-30
Click the Ubuntu icon at the top left corner and search for "Startup Applications". The dialog will be pretty self explanatory.

---

### Post by biomedtek on 2011-04-30
Did it, thanks, issue closed.
Hey can I ask you *one more thing, in gnome it is possible to auto-hide the menu bar, is it also possible in unity? I would like to also hide the launcher, and have them pop out when I move the cursor to the edge of the screen.* I have a thing about keeping a clean desktop.

---

### Post by chenxiaolong on 2011-05-01
The top panel cannot be hidden, but the launcher can. You need to install the "compizconfig-settings-manager" package. After you install that, search for "Compiz" in the Unity launcher and open the Compiz manager. Now, in the Compiz manager, find the "Ubuntu Unity Plugin." There, you will have a lot of options to change, including autohide, launcher size, transparency, etc.

---

### Post by pipolibo on 2011-05-02
Maybe this helps:

"
This is due to #761326, wicd doesn't support the the application indicators. The workaround is to use

wicd-client -n

and a gtk window will pop up. Everything works then.

"

From [https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/758019](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/758019)

---

### Post by biomedtek on 2011-05-02
yeah, I added wicd-client to the start up apps, and the indicator appears at log on automatically. A simple fix for a vexing problem.

---

