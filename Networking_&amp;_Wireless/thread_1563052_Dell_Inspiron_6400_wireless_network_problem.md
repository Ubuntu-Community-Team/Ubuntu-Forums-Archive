---
title: "Dell Inspiron 6400 wireless network problem"
date: 2010-08-28
forum: Networking &amp; Wireless
---

### Post by furiston on 2010-08-28
Hi,
I'm a new ubuntu user and i have lucid on my laptop inspiron 6400. But i have a problem to activate my wifi device. normally this inspiron 6400s does not have an extra switch to activate wireless network, there is function key to make it. Fn+F2 activate wireless network, but it does not function when i boot ubuntu. i wonder if there is anyone to guide me step by step to make it. thanks...

---

### Post by ieee488 on 2010-08-28
Fn+F2 is for Windows.

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by ddoxey on 2010-11-07
Similar problem on my (wife's) Dell Inspiron 1545 (shipped with Ubuntu). The wireless interface is toggled on/off with MS+F2, where MS is the windows logo key.

Occasionally my wife says, "Honey, my network doesn't work again." (I'm sure this is because she allows the cat to walk on her keyboard.) The visible symptom is the wireless icon has the red exclamation point on it.

There's no question that the hardware is supported because usually it works. 

Strangely, just hitting MS+F2 again doesn't bring the wireless icon back to a normal state. :(

In my searching, I found this somewhat relevant post:
[http://ubuntuforums.org/showthread.php?t=1503538](http://ubuntuforums.org/showthread.php?t=1503538)

The key discovery here is how to use the **rfkill** command.

```
:$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Using **rfkill** gives you a clue as to the state of the wireless hardware without depending on the icon which only tells you that the network connection is disrupted.

Evidently, the problem is that the network connection is not automatically resumed as soon as you re-enable the wireless hardware.

My solution:
[LIST=1]
[*]verify with rfkill that the wireless is not in blocked state
[*]use MS+F2 to change the state if needed
[*]restart networking services manually
[/LIST]

If you're not sure how to restart the network manually, you could just reboot. But I prefer to do:

```
sudo /etc/init.d/networking restart
```

I noticed that the icon lags. After the restart you could ping something and see that networking is active, yet the icon will take 10 to 30 seconds before it starts the spinning, and another 10 to 30 before is resumes normal state again.

I hope this helps with the 6400.

---

