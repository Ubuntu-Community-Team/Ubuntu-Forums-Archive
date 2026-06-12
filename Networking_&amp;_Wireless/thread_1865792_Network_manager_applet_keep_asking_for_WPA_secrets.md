---
title: "Network manager applet keep asking for WPA secrets"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by visualus on 2011-10-20
Hi Guys,
I've made an distro upgrade 11.04->11.10, but now my network-manager apllet is freaking out.

I was using the kwallet service to store all wireless passwords, now when I log in the dialog for opening kwallet is up (normal: network manager is trying to auto connect),
then when I enter the password a network nmanager popup is being showed to enter secret to my network.

I did it several times (even changed password storing to unencrypted file) but still it keeps asking for WPA secrets.
Even when I connect, and then click again on network ssid it asks for password again.

I'd be very grateful for any tips and helps, my wpa pass is kida randomly generated so it's really annoying to enter it every time i log in...

---

### Post by mibu.kyoshiro on 2011-11-01
Same issue here. KDE Network Manager Applet was not willing to use the stored password information for existing connections. Also, it did not show them on the managing tab for wireless connections.

I did the following to get out of this:

1. Saving previous connects to a point of ones choice to restore them in case you have not saved the credentials in your head [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

```
cp-a ~/.kde/share/apps/networkmanagement/connections ~/Desktop 
```2. Remove all previous installed package remains not needed any more. Advice: Please check the list of packages before removing unchecked!

```

# Check packages first:
dpkg -l | grep ^rc | awk '{ print  $2 }' | sudo xargs echo
# Remove if you're sure:
dpkg -l | grep ^rc | awk '{ print  $2 }' | sudo xargs dpkg -P
```3. Set credentials saving in knetwork manager applet to "Store connection secrets" In file (unencrypted)
4. Connect to your connections and enter the credentials. The secrets should be saved again.
5. Check storing of the credentials by logout and login again.

I could not check for sure which of the above steps did the trick, but it worked for me. :)

---

### Post by Nir Friedman on 2011-11-02
How do I double check which of these packages are needed? Why are these packages not removed when I do sudo apt-get autoremove or autoclean?

---

### Post by mibu.kyoshiro on 2011-11-03
> **Nir Friedman said:**
> How do I double check which of these packages are needed? Why are these packages not removed when I do sudo apt-get autoremove or autoclean?

The packages listed by the command:
```
dpkg -l | grep ^rc
```
are packages installed previously and configured automatically or manually on or after installation time. After the update these packages have been removed. You can double check this examining the logfile /var/log/dpkg.log or /var/log/dpkg.log.1 (or even similar, check the timstamps) if it has been rotated already.

The 'rc' at the beginning of the lines means there is a configuration file remaining even the packages have been removed already.

So even some packages have been removed, some remaining configuration files can have some side effects to newer packages. So the command mentioned in my previous posting cleans up some the system a bit more.

Hope this makes it a bit more clear. :o

---

### Post by Nir Friedman on 2011-11-03
After reading your last post, I ran the second line of code you had. It didn't break anything, but it didn't fix anything either. I am having a whole plethora of strange issues with the wifi that I suspect may be caused by weird holdovers in configuration files. I have another thread about it here ([http://ubuntuforums.org/showthread.php?t=1873458](http://ubuntuforums.org/showthread.php?t=1873458)) that I haven't been able to get anyone to respond to. Do you have any other suggestions?

Nir

---

### Post by elvisd on 2011-11-11
Same problem in GNOME

---

### Post by visualus on 2011-11-11
Actually I found kind of walk-around. 
In KDE NM applet you have to tick "System connection" when creating new wireless connection.
Then password is somehow stored and NM connects automatic.

---

### Post by Nir Friedman on 2011-11-17
I tried this work around and it worked for me too. Out of curiosity, does anyone know what the "system connection" thing does? Does it lead to data being stored somewhere other than /home? I have a suspicion that all these problems are due to old info not being wiped properly, info that would probably be stored in /home.

---

