---
title: "installing wireless without connection"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by ascira on 2010-02-18
hi,
i am quite new to ubuntu and have what might be simple problem.

i have only wireless connection and a netbook with working wireless, and a laptop with no wireless drive. they are both ubuntu. how can i install wireless on the laptop?
thanks for suggestions
aleksej

---

### Post by Jinji on 2010-02-18
Go to system>administration>hardware drivers and see if your wireless device shows up

---

### Post by katie-xx on 2010-02-18
> **ascira said:**
> hi,
i have only wireless connection and a netbook with working wireless, and a laptop with no wireless drive. they are both ubuntu. how can i install wireless on the laptop?
thanks for suggestions
aleksej
[SIZE=2][COLOR=Blue]
Your laptop ..do you mean it doesnt have a wireless card or do you mean it just isnt working?

Kate
[/COLOR][/SIZE]

---

### Post by ascira on 2010-02-21
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]
Your laptop ..do you mean it doesnt have a wireless card or do you mean it just isnt working?

Kate
[/COLOR][/SIZE]

thanks for replies. I am new here and i forgot to write the type of laptop: fujitsu siemens amilo la1703. In the meantime I got the wired connection and found the solution for the wireless from here [http://www.uprize.no/?q=node/1](http://www.uprize.no/?q=node/1)

---

### Post by KaiJordanDay on 2010-02-21
Goto Application -> Accessories -> Terminal 

type in 
> iwconfig

post what you see?

also type this

> lspci -v | less

post what you see.

---

### Post by ascira on 2010-02-23
> **KaiJordanDay said:**
> Goto Application -> Accessories -> Terminal 

type in 


post what you see?

also type this



post what you see.

thanks for the help. i did find the solution here [http://www.uprize.no/?q=node/1](http://www.uprize.no/?q=node/1)

---

