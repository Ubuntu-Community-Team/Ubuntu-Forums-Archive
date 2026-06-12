---
title: "Wifi password problem"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by frostwyrm333 on 2009-09-25
I have a problem connecting to my zyxel router. Ubuntu recognizes the network and it works all right in windows. But I have a problem when I want to connect to it. It uses WPA/WPA2 and the dialog seems to accept only 8 character password, but I have 6 character password. Is it intentional?
Thx for help.

---

### Post by spd106 on 2009-09-25
Most of the docs I have read about WPA specify a key between 8 and 63 characters. I'm not sure whether these are hard limits, but you will significantly lower the encryption strength by using less than 8 characters in your key. 

As a workaround, you can use a WPA hex generator such as the one at [http://www.xs4all.nl/~rjoris/wpapsk.html](http://www.xs4all.nl/~rjoris/wpapsk.html) to calculate the 64 digit hex string that Network-Manager uses.

Obviously, I would strongly recommend that you use a longer key.

---

### Post by frostwyrm333 on 2009-09-26
It won't take the hex string, I will try changing the password.

---

### Post by SporkD2 on 2010-04-07
Is there a fix for this? My company uses a less then 8 WPA2 key and ubuntu 9.10 wont let me connect to anything less then 8 digits.

Thanks

---

### Post by razinjap on 2011-05-06
Come on, my router just doesn't even support more than 5 characters. Do I really have to buy a new one if I want to use Ubuntu?! O_o

---

### Post by Radical Thought on 2012-02-15
My company has a 7 character password. I can't use the wireless. Is there a workaround? Maybe you can set any password when root?

---

### Post by gnulab on 2012-02-27
I'd say this is a bug... You can't possibly impose everyone to change their router(s). What if a public router issue password that's less than 8 characters?

---

