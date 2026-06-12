---
title: "Remote Controls"
date: 2012-06-14
forum: Mythbuntu
---

### Post by jlp_engineer on 2012-06-14
OK, here is an easy one :-)

I would like to have a remote that is similar to the PVR-150 MCE remote, that has a button for the guide while viewing TV.  With the remote I have now, which is a StreamZap remote, I have to press menu, then down arrow a few times, then press select twice, which is a pain.  I know I could define the colored buttons to do this, but the rest of my family is not as technically inclined as I am.  Also, how does LIRC know what kind of receiver is connected (UIRT, USB, etc.) when you select a remote from the list???  I am foggy on the relationships there. :confused:

So, is there a remote on the market, that has a guide button for live TV, that ideally already works with MythTV, that maybe even comes with its own USB IR receiver???  I would also like to have an IR Receiver that lights an LED so I know it is receiving a signal (the geek in me needs that :) ).  I have seen circuits for UIRT and UIRT2, and could build these.  I also like some of the USB circuits, but I am not wild about building the programmer for them.  The serial port receivers are simple and easy, but not too many PC's are being sold with serial ports on them these days.

Opinions?

TIA!!!

---

### Post by nickrout on 2012-06-14
This is the best remote i have ever used with mythtv:

[http://rtr.ca/sapphire_remote/](http://rtr.ca/sapphire_remote/)

It's keys are all assignable however you want. By default InfoEPG key is mapped to "i" (INFO in mythtv) and LiveTV is mapped to F16 (TV Guide in Mythtv). However you can assign them as you please.

It's damned cheap (USD13 delivered anywhere in the world!) and the driver works well. The author is often updating and improving it. 

So not quite what you are after, but I recommend giving it a try  as $13 isn't much to waste if you don't like it.

---

### Post by alien878 on 2012-06-15
I am very happy with my Logitech Harmony 600.  If you have a remote with enough keys, you can program them on the Harmony.  Ex. program the "Info" key to act like the "green" key on your old remote.  That way you won't have to mess with setting up a new IR receiver.  The added advantage is it can replace most, if not all of your other remotes.

They are normally a little pricey, but I was able to pick mine up on sale for 30 Euro.

---

### Post by jlp_engineer on 2012-06-16
Nick,

The sapphire remote looks good.  Does the receiver give you feedback with an illuminated LED?  Also, is the remote and receiver supported in 12.04, or do you have to load the driver the author speaks about?

---

### Post by jlp_engineer on 2012-06-16
Any other ideas folks?   

What remote are you using and why do you like it?

USB receiver?

Serial home built receiver?

---

### Post by nickrout on 2012-06-16
> **jlp_engineer said:**
> Nick,

The sapphire remote looks good.  Does the receiver give you feedback with an illuminated LED?  Also, is the remote and receiver supported in 12.04, or do you have to load the driver the author speaks about?

No feedback.

Driver is not in the kernel or packaged for mythbuntu. However installation is as easy as it says on his web page, download, tar xzvf, cd , sudo make install

Works straight away, no need for reboot.

---

### Post by TrueBlueBlooded on 2012-06-21
[http://store.hauppauge.com/accessories2.asp?product=mce_remote](http://store.hauppauge.com/accessories2.asp?product=mce_remote)

Works with the lirc mceusb driver and the IR receiver has an activity LED.

---

### Post by anonymousdog on 2012-06-21
> **TrueBlueBlooded said:**
> [http://store.hauppauge.com/accessories2.asp?product=mce_remote](http://store.hauppauge.com/accessories2.asp?product=mce_remote)

Works with the lirc mceusb driver and the IR receiver has an activity LED.

In the mce remotes, I prefer the [Pinnacle's transceiver]("http://www.amazon.com/Pinnacle-Remote-Windows-Media-Center/dp/B000WR2E00"); I've had two of the above fail over time while the Pinnacles keep going strong.

However, I've abandoned all IR remotes out of unresolved frustration, in favor of RF mini-keyboards like the one I reviewed in the ["Please post your Functional/Non Functional Hardware" thread]("http://ubuntuforums.org/showpost.php?p=12023940&postcount=350").  I still use mce transceivers for blasting (which they perform very reliably).

---

### Post by jlp_engineer on 2012-06-21
Good suggestions everyone...  I have some research to do on them to see how well each is supported in MythTV.  

I have another related question, so I am hoping some one reads this and can answer this one:

What keyboard button do you press to bring up the EPG (listings) while you are watching LiveTV.  The command key reference for MythTV says this is the letter "M", but when I press this, all I get is a menu.  Don't want the menu!  I want the TV listings.  Same as what the PVR-150 remote gives me when I press the button labeled "guide".  Is it an unlisted key or sequence?

---

### Post by Lester_Burnham on 2012-06-21
Hi,

To see what is actually set. Fire up mythweb and navigate to http://<your IP>/mythweb/settings/mythtv/keys
On mine. It's capital "S"

You can add your own key combo's, but you also need to map the keys to remote buttons in /.lirc/mythtv

Have a look in this MCE lirc file
[http://www.mythtv.org/wiki/MCE_Remote_LIRC_Config]("http://www.mythtv.org/wiki/MCE_Remote_LIRC_Config")

Lester

---

### Post by anonymousdog on 2012-06-22
This [RF version of the mce remote]("http://www.newegg.com/Product/Product.aspx?Item=26-641-002&SortField=0&SummaryType=0&Pagesize=10&PurchaseMark=&SelectedRating=-1&VideoOnlyMark=False&VendorMark=&IsFeedbackTab=true&Page=2#scrollFullInfo") looks super intriguing.  Made by Tripp Lite; so, it's probably good hardware.  Supported by the mceusb driver (according to some web posts I found) although the manufacturer disclaims this.

---

### Post by jlp_engineer on 2013-01-07
Does anyone know of a remote/receiver combo that just plugs in and works 100%?  As the first post in this thread indicates, I am using the Streamzap remote, but trying to modify LIRC config files resulted in a nearly inoperable remote.  I still don't really know what I did wrong, but I was hoping I didn't have to go back through that again.  

I have seen some posts about remotes that are seen as USB keyboards by the OS, but configuring xmod, and certain other shortcomings has me a little concerned.  I would not be concerned about modifying LIRC to get my Sreamzap working like I want, but I don't want to end up with a non-working remote again.  Is there one source that can tell me what files to modify, where they are located, and what the base content needs to be???   I understand that the configuration files cannot be 100% what I want, but something should be out there that gets me to 90% or better.

Thanks for your wisdom....

---

### Post by AlecJ on 2013-01-07
Any one of these work out of the box

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

I have the 1039 5/5 which can learn from the TV remote to turn the TV on and off.

If you run ```
irw
``` from a terminal, then press buttons on the remote, the name of the button is displayed in the terminal.
I cut and pasted these into a file and printed it.
Once you know the name of each button you can edit ~/.mythtv/lircrc to the change what the buttons do.
I use mousepad to edit as it's graphical
```
sudo apt-get install mousepad
sudo mousepad ~/.mythtv/lircrc
```The keys for the functions are in set in the setting menu of the frontend as well as mythweb.

you will see where and what to change in ~/.mythtv/lircrc remember to edit with sudo and save a backup before making any changes.

an example from my files for the Guide button
irw
```
000000037ff07bd9 01 Guide mceusb
```entry in ~/.mythtv/lircrc note the remote is mceuse yours will different.
```

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end
```

hope this helps

---

### Post by nickrout on 2013-01-07
> **jlp_engineer said:**
> Does anyone know of a remote/receiver combo that just plugs in and works 100%?  As the first post in this thread indicates, I am using the Streamzap remote, but trying to modify LIRC config files resulted in a nearly inoperable remote.  I still don't really know what I did wrong, but I was hoping I didn't have to go back through that again.  

I have seen some posts about remotes that are seen as USB keyboards by the OS, but configuring xmod, and certain other shortcomings has me a little concerned.  I would not be concerned about modifying LIRC to get my Sreamzap working like I want, but I don't want to end up with a non-working remote again.  Is there one source that can tell me what files to modify, where they are located, and what the base content needs to be???   I understand that the configuration files cannot be 100% what I want, but something should be out there that gets me to 90% or better.

Thanks for your wisdom....
This is not strictly out of the box, but as near as dammit, you have to download a driver and compile it - but once you have done that it is flawless.

I have 7 of them (including spares).

[http://rtr.ca/sapphire_remote/](http://rtr.ca/sapphire_remote/)

---

### Post by topcat5 on 2013-01-08
My recommendation is go get a flirc.tv IR receiver.  It converts any remote's signals directly to keycodes.    You cam map almost any remote with it. You don't need lirc at all as the CPU will see it as a keyboard.  It's very responsive, there are ubuntu drivers and you can get support for linux on their website. 

My recommendation for a remote to look for a OEM logitec harmony 650.  It has all the buttons needed for Mythtv, it's well constructed, and the keys light up which is perfect for the bedroom.  This has the added bonus that you can control the volume and tv power directly.  You can sometimes find these for $39 or less.  Well worth it in IMO.  

It's not quite plug and play, but it's close.

---

### Post by jlp_engineer on 2013-01-20
> **AlecJ said:**
> Any one of these work out of the box

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

I have the 1039 5/5 which can learn from the TV remote to turn the TV on and off.

If you run ```
irw
``` from a terminal, then press buttons on the remote, the name of the button is displayed in the terminal.
I cut and pasted these into a file and printed it.
Once you know the name of each button you can edit ~/.mythtv/lircrc to the change what the buttons do.
I use mousepad to edit as it's graphical
```
sudo apt-get install mousepad
sudo mousepad ~/.mythtv/lircrc
```The keys for the functions are in set in the setting menu of the frontend as well as mythweb.

you will see where and what to change in ~/.mythtv/lircrc remember to edit with sudo and save a backup before making any changes.

an example from my files for the Guide button
irw
```
000000037ff07bd9 01 Guide mceusb
```entry in ~/.mythtv/lircrc note the remote is mceuse yours will different.
```

begin
    remote = mceusb
    prog = mythtv
    button = Guide
    config = S
    repeat = 0
    delay = 0
end
```

hope this helps

Yes, this did help.  Thank you very much.  This is the first time I have tried something with regard to LIRC and it worked.  The Wiki for this remote seems to indicate that you change two files (lircrc & lircd.conf), which I did.  Once I did that, my remote didn't work.  

Thanks again.

---

