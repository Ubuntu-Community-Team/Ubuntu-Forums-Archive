---
title: "nm-applet in natty: GUI problem - grey bar, no text"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by carbon512 on 2012-03-01
I've had no problems with network manager since I updated to natty -- except one: Periodically when I click in the nm applet display in my notification area, and then move down the list that comes up and select "VPN connections,"  I just see a thin grey horizontal line instead of the normal list from which I can choose and start my VPN connection.
Thus, I can't connect to the VPN connection required by my wireless connection at work, can't use wireless.

Current two solutions are:
1 - open terminal, use commands:
```
killall nm-applet
nm-applet
```This works and I can then use the nm applet normally -- I just have to remember to keep that terminal session open because closing it closes network manager

2 - restart computer

Both these solutions have their obvious drawbacks. Is there a better solution? Does anyone else have this problem? It is not an actual network connectivity problem, just an inability to access the network connection options.

---

### Post by Paddy Landau on 2012-03-02
I don't know how to solve your problem, but here is how you can start nm-applet without holding a terminal open.

Here are three different options. Choose whichever appeals to you most.


[LIST=1]
[*]Use Alt-F2. Instead of typing *nm-applet* into the terminal, press Alt-F2 and type it there. (You can also type *killall nm-applet* there.)
[*]When you type it in the terminal, add an ampersand, thus:
```
nm-applet &
```If for some reason that doesn't work, then use the following more complicated command:
```
nohup nm-applet &>/dev/null &
```
[*]Create a script to run those commands and add it to your launcher or to a keyboard short-cut.
[/LIST]


I hope that helps; let's hope someone with more knowledge can help you solve the problem in the first place.

---

