---
title: "Create/ connect to ad hoc network"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by Falc7 on 2010-04-20
I am struggling to create or connect to an ad hoc network with Kubuntu 9.10, KDE 4.4.

I click on the knetwork manager icon -> create network connection -> new ad hoc network. But then nothing happens.

I've also googled around, but haven't found anything useful yet.

---

### Post by Falc7 on 2010-04-27
bump, when i try to connect to an ad hoc network, it just comes up with the password box after 2 mins trying to connect. I am sure the password is right however as i made it 11111111

---

### Post by 4ebees on 2010-05-20
> **Falc7 said:**
> bump, when i try to connect to an ad hoc network, it just comes up with the password box after 2 mins trying to connect. I am sure the password is right however as i made it 11111111


You're not the only one stuck here.

If I find a solution, I'll post it back here.

:)

---

### Post by 4ebees on 2010-05-20
> **Falc7 said:**
> bump, when i try to connect to an ad hoc network, it just comes up with the password box after 2 mins trying to connect. I am sure the password is right however as i made it 11111111

Okay. This works.

However,if you're using Wicd you need to change the part where is says:

sudo /etc/dbus-1/event.d/25NetworkManager stop

to 

sudo /etc/dbus-1/system.d/wicd stop


And if you're using wireless LAN then eth0 become wlan0

This should then work.

Also, to turn off these settings I imaging (have yet to try it :)) you would:

Stop wicd
Stop the wlan0

then

sudo iwconfig wlan0 mode managed

If that's your normal setting.

I'd suggest you check your normal setting first by running:

iwconfig

in the command line to see what your normal settings are.


See how you go.

---

### Post by Falc7 on 2010-05-26
sorry i am not quite following.
So first i run:
iwconfig
then?


I am using the defualt wireless network manager in kubuntu

---

### Post by 4ebees on 2010-05-27
> **Falc7 said:**
> sorry i am not quite following.
So first i run:
iwconfig
then?

I am using the defualt wireless network manager in kubuntu


Sorry for the delay in getting back to you.


:)

I'm trying to work out how to make it simpler :)))

The first thing you do is open a terminal or konsole (as it's named in Kubuntu/KDE), then follow the instructions below.

There is no graphic user interface (GUI) 'clicking' going on here, my friend. Even though that's usually my preferred method.

So, take a deep breath and open a terminal/konsole and see how you go :)

Get back to me with the result and we'll see where we can go.

If there are problems, please make some very specific notes as it will help me to understand what's happening.

---

### Post by pennygov on 2010-06-03
What "instructions below"?:confused:

---

### Post by 4ebees on 2010-06-03
> **pennygov said:**
> What "instructions below"?:confused:

Hi there,
You need to look 'up' the page further. Two weeks ago I outlined how to create the settings. You'll find the information in that post, above all these posts :)

---

