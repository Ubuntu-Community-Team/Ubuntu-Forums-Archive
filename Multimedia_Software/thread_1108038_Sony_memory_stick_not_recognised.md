---
title: "Sony memory stick not recognised"
date: 2009-03-27
forum: Multimedia Software
---

### Post by gewitty on 2009-03-27
Does anyone know if there is a solution to the problem of Sony memory sticks not being recognised when plugged into a card reader?

I believe that this may be a driver problem. I've tried the sticks on two different machines, both running Hardy, and neither of them even sees that a card has been inserted.

It's a rather urgent problem, as the cards were accidentally erased and I need to run Photorec to recover the pictures.

Any help or suggestions would be appreciated.

---

### Post by aeiah on 2009-03-27
have they ever worked under linux? a lot of memory sticks and cards have hidden partitions and stuff for encryption under windows, or backup/sync software etc and this can confuse linux. the solution is to just wipe everything and create a new partition but of course, you wont want to do that if you're trying to rescue files :p

does the card show up in /dev/? if so, you should do a dd copy of it, which will do a bit-for-bit copy. then at least any messing around wont wreak more havoc.
```

dd if=/dev/sdc1 of=~/sony_card_dump.img

```
this will create an image of sdc1 in your home directory. you'll probably need to be root though so bear in mind where your home dir will be. i of course dont know if sdc1 is your actual sony card partition.

i know this doesnt solve your problem per se but it'll ensure your data is safe and perhaps even gives you the opportunity to run photorec or something.

---

### Post by Maheriano on 2009-03-27
I had this issue before, the card would fit into a slot for another type of card and therefore wouldn't be recognized. Check the type of card it is and then check the symbols on the card reader to see if it supports that type. It's likely a SDHC card that's sliding into a SD slot.

---

### Post by blackened on 2009-03-27
Does this apply to your problem -> [https://answers.launchpad.net/ubuntu/+faq/312]("https://answers.launchpad.net/ubuntu/+faq/312")?

---

### Post by gewitty on 2009-03-27
> 

does the card show up in /dev/? if so, you should do a dd copy of it, which will do a bit-for-bit copy. then at least any messing around wont wreak more havoc.


No. In fact, the card reader light even fails to come on when I insert the card.

>  Check the type of card it is and then check the symbols on the card reader to see if it supports that type. It's likely a SDHC card that's sliding into a SD slot.

I'm pretty sure that the card is a standard memory stick. It's a Sony and the writing on the card says ' Memory Stick PRO' 512MB Magic Gate'

>  Does this apply to your problem -> [https://answers.launchpad.net/ubuntu/+faq/312?](https://answers.launchpad.net/ubuntu/+faq/312?) 

It may do. I'm not sure if the card readers I tried are using the Ricoh controller though (one is a Trust 610 USB reader, the other is a built-in unit of indeterminate make).

Looks as if I'm stuck :confused:

---

### Post by blackened on 2009-03-27
> **gewitty said:**
> It may do. I'm not sure if the card readers I tried are using the Ricoh controller though (one is a Trust 610 USB reader, the other is a built-in unit of indeterminate make).

Looks as if I'm stuck :confused:

I've never had any luck with Memory Sticks in Ubuntu. Seems I always have the totally unsupported hardware as well. Luckily the only one I have is in my phone and can be accessed through the phone's USB interface or through bluetooth.

---

### Post by Maheriano on 2009-03-28
Plug them into a Windows machine and remove them safely. Then plug them into the Linux box again.

---

### Post by ckonestroh on 2009-05-19
why can't you use this device?   

[http://www.keenzo.com/showproduct.asp?M=TRENDNET&ID=536401&ref=GB]("http://www.keenzo.com/showproduct.asp?M=TRENDNET&ID=536401&ref=GB")


Well got to run....

---

