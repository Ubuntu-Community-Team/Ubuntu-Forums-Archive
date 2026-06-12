---
title: "I have Ubuntu 10.10 and a Broadcom Chip.. Wireless won't work?"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by willswisher on 2010-12-14
Hello I am using a Dell Inspiron 1750 and my wireless card is Dell Wireless 1397 WLAN Mini-Card which I've read elsewhere is a Broadcom 43xx Legacy (absolutely no idea what that means) when I load Ubunutu it says firmware not installed for wireless.. I have absolutely no knowledge of computers or Linux but wanted to try an alternative to Windows.. can someone help me get Wireless Working... HELP PLEASE!!! And Don't tell me to enter some code without VERY DRAWN OUT Details of how to get to the place to enter some code and how to do it.. I really am new!!!!

Oh.. btw.. My wireless works perfectly on Windows 7 still. 

Thanks in advance,

I really love Ubuntu and hope I'll be able to use it when I get wireless going.

---

### Post by freshmeatz on 2010-12-14
plug it in to a wired connection, download the updates fully, then it should find it

or try putting the cd back in the drive and open a terminal and type this

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by willswisher on 2010-12-14
> **freshmeatz said:**
> plug it in to a wired connection, download the updates fully, then it should find it

or try putting the cd back in the drive and open a terminal and type this

```
sudo apt-get install bcmwl-kernel-source
```

I did manage to find bcmwl-kernal-source on my CD... i clicked it and it showed "Dependency not satisfiable: dkms"  tho I don't know how to "open a terminal" yet... like I said.. not kidding about the 100% newb part ;)

*Edit: Forgot to mention I lack a ethernet cord at the moment...

---

### Post by willswisher on 2010-12-14
ok found terminal and tried it.. said it wasn't found.. if i need to switch drives to that drive i dunno how to in terminal.

---

### Post by bkratz on 2010-12-14
> **willswisher said:**
> ok found terminal and tried it.. said it wasn't found.. if i need to switch drives to that drive i dunno how to in terminal.

I believe he/she wanted you to go to the menu at the top of the screen (in Ubuntu)

System
Administration
Software sources 

and put a "tick" in the box labeled "installable from CD Rom"

---

### Post by willswisher on 2010-12-14
nothing called Software Sources under Admin

---

### Post by bkratz on 2010-12-14
> **willswisher said:**
> nothing called Software Sources under Admin



I do run 10.04 and really don't remember doing anything to add that? Anyway another way to get there would be to go to 

System
Administration
Synaptic Package Manager

Then select
Settings
Repositories

and check install from CD there, sorry

---

### Post by Megaptera on 2010-12-15
I've used this simple fix on my Dell Inspiron laptop. Ignore the ref. to Dell Mini, this option worked for me if that's any help?

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by willswisher on 2010-12-15
We're getting somewhere.. not there yet tho :( 

I did tick the CD thing and the second i did a broadcom message shot up.. tried to activate it.. got this message 

Failed to Fetch CDROM:[Ubuntu.10.10.Maverick Meerkat_- Release i386 *20101007) /pool/main/p/patch/patch_2.62-Ubuntu1_i386.deb File not found


or something like that.. as i have to keep switching to Windows to post here can't cut and paste.. 

tried through terminal.. no dice

tried loading up the bcmwl-kernal-install from the CD itself said failed to connect to the internet.. guess it needs to be connected :(

---

### Post by willswisher on 2010-12-15
as for the other person..

"First you have to physically connect the Mini/Vostro to a wired internet connection. This step is a must."


my dog chewed up my Ethernet cord...

---

### Post by wheelyfeet on 2010-12-15
I'm an absolute newbie too. Here's what worked for me.  Make sure you are connected to the internet (going to have to get hold of an ethernet cord somehow) then go to applications and click on the "additional drivers" icon. You should get an option for Broadcom 43 wireless driver. Click on activate.  I hope additional drivers is there for you. You evidently weren't connected to the internet on install so I have no idea what might be different because of that.

I just read that the Broadcam 43 driver may not work with a legacy chip.  Here's a site to check out that goes in to detail about broadcom drivers.  [http://bit.ly/coyPee](http://bit.ly/coyPee)

---

### Post by Megaptera on 2010-12-15
> **willswisher said:**
> 
my dog chewed up my Ethernet cord...

I would expect that you could borrow one. Buying one would be an investment too. 

Perhaps get your dog some 'doggie treats' for Xmas to stop him eating your hardware? :p

---

### Post by bkratz on 2010-12-15
You might want to go through this information

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

See the section labeled
"STA - No Internet access"

---

