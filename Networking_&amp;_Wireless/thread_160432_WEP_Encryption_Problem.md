---
title: "WEP Encryption Problem"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by Mr_Welfare on 2006-04-14
Hi Everyone,

I am running ndiswrapper and have successfully installed the windows drivers for my D-Link GWL-122 (A2). After a few hours of troubleshooting, I finally got my internet connection to work by removing the WEP Encryption on my D-Link DL-524 router. I don't really like running on an unsecure internet connection, so when I enabled the WEP encryption again, my internet couldn't connect. (I have entered my WEP key correctly the System>Administrator>Network Settings>wlan0>Properties, but I still can't get it up and running. I have also tried to put dashes after every fourth digit in the WEP code like someone who posted on another thread said to do, but that didn't work either.) I've heard that the GUI Network Settings encryption system is a little buggy and that it would be better to manally enter your code through the terminal. How would I go about doing this?

If anyone has any help, it would be greatly appreciated.

Thanks,

Mr_Welfare

---

### Post by Jason_25 on 2006-04-14
You heard right.
```

sudo iwconfig wlan0 key insertkeyhere

```

---

### Post by Mr_Welfare on 2006-04-14
[QUOTE=Jason_25]sudo iwconfig wlan0 key insertkeyhere[/QUOTE]

Ok. I tried what you said, didn't get any errors, restarted, and still the light on my USB adapter just blinks. I still can't seem to get a connetction. Is anything else that I might not have done yet that is causing the internet connction to crash?

---

### Post by Jason_25 on 2006-04-14
What is the output of iwconfig once you have entered the key?  It should connect as soon as you enter the key, no rebooting should ever be required.

---

### Post by Mr_Welfare on 2006-04-15
[QUOTE=Jason_25]What is the output of iwconfig once you have entered the key?  It should connect as soon as you enter the key, no rebooting should ever be required.[/QUOTE]

There isn't any output at all. The terminal just asks for my password, and after entering it and hitting enter, the *username*@Ubuntu/~ <== (Sorry if I'm not quite accurate there) Comes up.

Note:

I don't know if this makes a difference or not, but I think I'm using a 128 bit WEP code (its 26 digits long) and I'm not putting dashes between every fourth character

---

### Post by Mr_Welfare on 2006-04-16
Now I've seen that the two threads I started about different things have merged into two different thread about the same thing. If anyone has any help, it would be great. (For links to the two threads, see my signaure.)

Mr_Welfare

---

### Post by kinggreen on 2006-04-16
[QUOTE=Mr_Welfare]There isn't any output at all. The terminal just asks for my password, and after entering it and hitting enter, the *username*@Ubuntu/~ <== (Sorry if I'm not quite accurate there) Comes up.

Note:

I don't know if this makes a difference or not, but I think I'm using a 128 bit WEP code (its 26 digits long) and I'm not putting dashes between every fourth character[/QUOTE]

hi well im using a MSI cb54g2  wireless  card that "works out of the box" and i never did get the 128 bit WEP working but i used the 64 bit WEP entered via the gui and it worked first time, not the right solution but a solution anyway.
colin.

---

### Post by YuHoo on 2006-04-16
If it is 26 characters long you're using HEX keys I believe. That means that when you go into the networking you need to use that instead (obviously). I never got the HEX passcodes to work with my laptop. Instead I used the 13 character ASKII passcode.

ndiswrapper might also not support all the features of your card. I would check what D-Link is offering in the form of experimental drivers [http://support.dlink.com/faq/view.asp?prod_id=357](http://support.dlink.com/faq/view.asp?prod_id=357)

---

