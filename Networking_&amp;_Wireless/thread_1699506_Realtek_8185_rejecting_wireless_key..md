---
title: "Realtek 8185 rejecting wireless key."
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by Omega88 on 2011-03-03
Just installed ubuntu on my computer, but when I try to connect to my wireless I type in my password and it doesn't connect.

It says its WPA/WPA2 and won't let me change that (I am not sure what mine actually is) 

Im using a virgin media 'superhub' to connect but have changed the default wireless password.

Any help?

Thanks

---

### Post by Omega88 on 2011-03-04
Ok it is definitely WPA2, but it just won't accept my password and connect. it is picking up all wireless connections, just not connecting, and claiming the password is wrong.

---

### Post by Niedzwiedz on 2011-03-04
when I first connected to my Linksys router I used the; System > Preferences > Network Connections
This did not work for me!
I seen the Wireless icon top right that is left of the Date.
Click > Connect to Hidden Wireless Network... > Network Name & Wireless Security + Passphrase

Now; be sure you using an actual password WPA security or whatever. If, you never set this up then you probably using no security. Entering the password to get into Admin of the router not what you enter. I not sure, but, may just leave it all blank and select the router you wanting???

---

### Post by GreeTufty on 2011-06-21
Hi Everyone,
  I am also a virgin media user who has had severe problems with wireless for the last few hours after an upgrade.  I noted many forum posts indicating some success with de-activating security on the router.  This worked for me (details of how to access my router were written on it, ie IP, Username and password).

However, not wanting an unsecured network, I added a WEP key, which worked, but my friends Windows 7 turned its nose up at it.

I then noticed that in my router there are 2 options for WPA personal:
1. WPA2-PSK[AES]
2. WPA-PSK[TKIP] + WPA2-PSK[AES]

I switched to the first option, and now all is well- It must've been on the second option originally, no wonder Linux got confused

---

### Post by bkratz on 2011-06-21
> **GreeTufty said:**
> Hi Everyone,
  I am also a virgin media user who has had severe problems with wireless for the last few hours after an upgrade.  I noted many forum posts indicating some success with de-activating security on the router.  This worked for me (details of how to access my router were written on it, ie IP, Username and password).

However, not wanting an unsecured network, I added a WEP key, which worked, but my friends Windows 7 turned its nose up at it.

I then noticed that in my router there are 2 options for WPA personal:
1. WPA2-PSK[AES]
2. WPA-PSK[TKIP] + WPA2-PSK[AES]

I switched to the first option, and now all is well- It must've been on the second option originally, no wonder Linux got confused

Ubuntu does seem to get a little confused sometimes when you are broadcasting in mixed mode. Either one or the other, but not both, usually works.

---

### Post by chili555 on 2011-06-21
> **bkratz said:**
> Ubuntu does seem to get a little confused sometimes when you are broadcasting in mixed mode. Either one or the other, but not both, usually works.plus one thousand

My colleague bkratz is, as usual, exactly correct, all you searchers!

---

### Post by Pipps on 2012-07-06
> **GreeTufty said:**
> Hi Everyone,
  I am also a virgin media user who has had severe problems with wireless for the last few hours after an upgrade.  I noted many forum posts indicating some success with de-activating security on the router.  This worked for me (details of how to access my router were written on it, ie IP, Username and password).

However, not wanting an unsecured network, I added a WEP key, which worked, but my friends Windows 7 turned its nose up at it.

I then noticed that in my router there are 2 options for WPA personal:
1. WPA2-PSK[AES]
2. WPA-PSK[TKIP] + WPA2-PSK[AES]

I switched to the first option, and now all is well- It must've been on the second option originally, no wonder Linux got confused

This worked for me too - thank you! :)

(Using Ubuntu 12.04 and a Virgin  DGN1000SP wireless router.)

---

