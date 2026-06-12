---
title: "Setting up DSL wired connection"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by canadianwriterman on 2009-03-18
I'm still having network problems that I can't seem to resolve, so I'm posting a bit of a description in the hopes that someone has experienced this before.

**_Background_**

I've been using Ubuntu for several years and am currently running 8:10. I had a DSL account all that time and, whenever moving the machine or doing a fresh install of Ubuntu, all I had to do was plug in the DSL cable and Ubuntu automatically detected the connection. It was displayed as "Auto eth0" in Network Manager and connection to the etherworld fine with no further action.

Now I have moved and had to open a new DSL account with the same ISP. This included a new wired DSL modem. I had to set up the modem from within Ubuntu, including a password and username.

**_Current Situation_**

When booting up, Network Manager reports that it has connected through "Auto eth0" but there is no actual connection to the outside world. I had to use the DSL tab in Network Manager to set up the DSL connection, including adding the username and password. I never had to do this before. Now when I boot up, I always have to do the following which is completely different from how it always worked before:

[LIST=1]
[*]Wait for the Auto eth0 connection advisory
[*]Click on the NM icon and select "DSL Connection 1"
[*]Enter a password in the keyring popup
[*]Wait for a connection to "DSL Connection 1"
[/LIST]

Everything works until I reboot and have to go through the whole process again. I tried deleting the "Auto eth0" connection from NM, but it returns on reboot. Also, I set the DSL connection to automatic.

**_Goals_**

Have the DSL connection recognized on boot automatically and stop having to select it manually in NM.
Stop having to enter a password in the keyring to access the DSL connection.

As I said, none of this happened in the past (even with 8:10) until I got a new DSL account. Any help would be greatly appreciated. Thanks.

---

### Post by barjoyai on 2009-04-26
hello guys..
i've the same problem as canadianwriterman but i'm on ubuntu jaunty..to canadianwriterman, perhaps you want to try sudo pppoeconf..i used to use sudo pppoeconf to connect to the internet automatically before with previous version of ubuntu..but with ubuntu jaunty, it just won't work automatically and i tried to connect thru network manager and it worked but eventhough i've set the dsl connection to connect automatically, it won't after each reboot..after i created the dsl connection and reboot, the auto eth0 connection is gone by itself..but i still have to click the icon to connect to the dsl connection..
hope somebody can help..

---

