---
title: "Network manager/wicd problems"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by whatthefunk on 2011-02-02
I just installed wicd to replace network manager (honestly, network manager is the most useless program Ive ever encountered).
The connection is now more stable, but its still very slow.  Could this be a driver problem?  Im using a Buffalo WLI-UC-GN USB adapter.  I havent fooled around with ndiswrapper yet, but its on my list...
Also, id like to get rid of network manager from the toolbar.  NM is not on my startup application list, but the icon is still there and connected in some way to the wicd program.  If I cancel the connection on NM, the connection on wcid goes as well.  Is there any way to stop this?
Thanks

---

### Post by whatthefunk on 2011-02-02
This is now causing crashes.  On the Task Bar, I have icons for both Network Manager and Wicd.  Network Manager will still loss the connection at times and then both network manager and Wicd try to find it again at the same time.  Everything freezes and I have to turn off the computer.

Is there some way to completely block Network Manager without purging it?

---

### Post by grahammechanical on 2011-02-02
Have you tried deleting the connections from Network manager?

Regards.

---

### Post by whatthefunk on 2011-02-02
> **grahammechanical said:**
> Have you tried deleting the connections from Network manager?

Regards.

How do you do that?

---

### Post by thefasterblueone on 2011-02-02
To completely remove NetworkManager run this in terminal

```
sudo apt-get purge NetworkManager
```

---

### Post by whatthefunk on 2011-02-02
I tried to remove it with the Package Manager and it said that it would also have to remove my desktop.  Will the command line purge do this too?

And, I dont know if I want to totally get rid of it...I just want to turn it off so that it wont interfere with wicd.

---

### Post by thefasterblueone on 2011-02-02
This will completely remove it but you can reinstall it using Ubuntu Software Center.

When you uninstall without "purge" it does not uninstall configuration files.
This command will uninstall NetworkManager and the configuration files, so that WICD can properly manage your connection.

This fixed my connection problems.

---

### Post by whatthefunk on 2011-02-02
When I try to purge, I get this message:

> The following packages will be REMOVED:
  lubuntu-desktop* network-manager* network-manager-gnome*


I dont want to loose my desktop.....

Is there another way to do this?

---

### Post by whatthefunk on 2011-02-02
After a couple more crashes, I decided to uninstall regardless of the lubuntu-desktop thing (a computer without a desktop is more useful than one with network manager...). No problems.  I purged and then had to run sudo apt-get install wicd again just to reconfigure everything and give it access to the keyring.  Wicd is working perfectly and I still have a desktop.  Thank god I got rid of that crap program...Debian should ditch Network Manager.

Thanks for the help, guys!

---

### Post by thefasterblueone on 2011-02-02
If you are still trying to fix your connection then maybe this link will reassure you that uninstalling all of NetworkManagers config files is ok to do, and will not uninstall your Desktop.

[https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/RemoveLubuntuDesktop]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/RemoveLubuntuDesktop")

---

### Post by helicase on 2011-02-02
> **whatthefunk said:**
> I decided to uninstall regardless of the lubuntu-desktop thing (a computer without a desktop is more useful than one with network manager...). No problems.
As far as understand it the (l)ubuntu-desktop package is safe to remove, because it is only a dummy package. It depends on all other desktop packages to make sure you have a complete desktop installed. Trouble is (as you have experienced with nm), if you want to uninstall one of those packages, it looks like you're going to remove the complete desktop. But luckily that's not the case.

---

### Post by tedwils on 2011-02-02
> **thefasterblueone said:**
> To completely remove NetworkManager run this in terminal

```
sudo apt-get purge NetworkManager
```
  Hi. I'm trying to remove network Manager as well in Ubuntu 10.10 but this code won't do it. Is it dependent on which directory you are in when the code is entered? Initially, I was in ted-desktop but that gave me "no such file or directory". I used search to locate Network Manager and found it in File System so I tried cd .. to get me to another directory and from there I tried cd /FileSystem but that wasn't working either. So I tried your code (cut and pasted) but still only get "no such etc.". Meanwhile, I have added Wicd to my system and I see it under Applications/Internet. I tried using it. My wired connection and wireless both showed up. I disconnected the "wired" and selected my SSID choice from the "wireless", it asked for the password, it was entered (correctly) and a few seconds later I got an error message "Connection Failed: Bad password.
Do you think this is happening because I still have Network Manager installed?

---

### Post by whatthefunk on 2011-02-02
> **tedwils said:**
> Hi. I'm trying to remove network Manager as well in Ubuntu 10.10 but this code won't do it. Is it dependent on which directory you are in when the code is entered? Initially, I was in ted-desktop but that gave me "no such file or directory". I used search to locate Network Manager and found it in File System so I tried cd .. to get me to another directory and from there I tried cd /FileSystem but that wasn't working either. So I tried your code (cut and pasted) but still only get "no such etc.". Meanwhile, I have added Wicd to my system and I see it under Applications/Internet. I tried using it. My wired connection and wireless both showed up. I disconnected the "wired" and selected my SSID choice from the "wireless", it asked for the password, it was entered (correctly) and a few seconds later I got an error message "Connection Failed: Bad password.
Do you think this is happening because I still have Network Manager installed?

For Ubuntu 10.10:

```
sudo apt-get purge network-manager
```

You have the exact same problem I had so I think this will solve it.

---

### Post by tedwils on 2011-02-03
Thanks WTF. I tried this and it did remove the network manager but it, or something else I did, messed up the top panel and the desktop. For that, I just finished reloading Ubuntu for a fresh start. One thing I learned with Wicd installed was the configuration for my wlan0 didn't like the password. This seems to be the area I have to work on. Thanks for your suggestion.

---

