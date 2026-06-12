---
title: "Has anyone got any remote to work?"
date: 2009-04-06
forum: Mythbuntu
---

### Post by itlarson on 2009-04-06
Ok, I know some of  the people on this forum have working remotes.  Could people please post what the use, and how they got it to work?  I can't seem to get a handle on what hardware might work, let alone how to set it up, so the more excruciatingly detailed the description, the better.

---

### Post by AboveTheLogic on 2009-04-06
This remote works fine for me:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16880121002](http://www.newegg.com/Product/Product.aspx?Item=N82E16880121002)

Just had to customize a few of the buttons but it seems to be doing well. I don't use the IR blaster, though.

---

### Post by nickrout on 2009-04-06
> **itlarson said:**
> Ok, I know some of  the people on this forum have working remotes.  Could people please post what the use, and how they got it to work?  I can't seem to get a handle on what hardware might work, let alone how to set it up, so the more excruciatingly detailed the description, the better.

microsoft mce remote and receiver. just used the settings in mythbuntu-control-panel.

---

### Post by newlinux on 2009-04-06
MCE receivers (with Harmony remotes emulating MCE remotes). I've had this working before mythbuntu-control-centre existed, so I've had lircd.conf and .lircrc files I made a while back - tweaked to my preferences.

What problems are you having? Really if you can get your receiver recognized you can use just about any remote. The main difference is whether config files for your remote already exist or if you need to make them. 

That said, if you want easy, pick one of the supported remotes with mythbuntu-lirc-generator or whatever it is called.

---

### Post by itlarson on 2009-04-06
What I really want to know is step by step how people got their remotes to work.  I have been trying to get a tira-2 usb receiver to work, but would consider buying new hardware if I could see a clear path to getting it working.

---

### Post by newlinux on 2009-04-06
> **itlarson said:**
> What I really want to know is step by step how people got their remotes to work.  I have been trying to get a tira-2 usb receiver to work, but would consider buying new hardware if I could see a clear path to getting it working.

I'm pretty sure I (and others) could help you get the tira-2 to work - is there a thread already for that? what remote are you using? 

Otherwise, step by step,  buy an MCE remote/receiver combo and go to mythtbuntu-control-center->Infrared devices, click enable remote control, select Windows Media Center Remotes, click generate dynamic button mappings, restart mythfrontend and done. Replace MCE remote/receiver with any supported hardware in that list...


Found the thread... I'll post there.

---

### Post by itlarson on 2009-04-06
Thanks- it looks like a lot of progress has been made since I chose the tira for my original suse myth box.  I will choose a remote from myuthbuntu control center if I can't get the tira to work.

---

### Post by Zeedok on 2009-04-06
> **newlinux said:**
> buy an MCE remote/receiver combo

I am a little confused by the wiki and the nomenclature.  Are the MCE remotes actual microsoft branded products, or is this a design template that other companies also use in producing remotes?

For example, will this [Hauppauge MCE remote]("http://www.i-tech.com.au/products/32142_Hauppauge_MCE_Remote_Control_Kit_.aspx") be as easy to setup as selecting Windows Media Center Remotes etc in Myth-control-center??  Has anyone successfully used this particular device?

I'm keen to have as smooth a set-up experience as possible . . .

---

### Post by boof1988 on 2009-04-06
> **Zeedok said:**
> I am a little confused by the wiki and the nomenclature.  Are the MCE remotes actual microsoft branded products, or is this a design template that other companies also use in producing remotes?

For example, will this [Hauppauge MCE remote]("http://www.i-tech.com.au/products/32142_Hauppauge_MCE_Remote_Control_Kit_.aspx") be as easy to setup as selecting Windows Media Center Remotes etc in Myth-control-center??  Has anyone successfully used this particular device?

I'm keen to have as smooth a set-up experience as possible . . .

That appears to be the same remote/receiver (included with Hauppauge HVR-1600) that I use.  It worked OOB (Mythbuntu 8.10).

I chose (in the MCC IR-setup) "*Windows Media Center Remotes (old version Microsoft USB ID)*"

---

### Post by Zeedok on 2009-04-06
Great.  Thanks very much, I'll give it a go.

---

### Post by newlinux on 2009-04-06
yeah there are a number of MCE remotes (some micro$oft branded, others from other brands). Most of the receivers will either use the mceusb (old) or mceusb2 driver.

[http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

---

### Post by DarkHam on 2009-05-25
please help me, it don't worlks for me, in ubuntu jaunty with ganyramote, and a nokia N70.
Bluetooth works fine in my ubuntu, i can send and receive files correctly, i set the bluetooth as hciconfig hci0 piscan.
I run ganyremote i chose totem, i run the client in the N70, i search the pc, i find 1 something, but i can't display it. i insert the bt address and i try, but nothing , don't works.
when i insert the bt address, my phone ask me if anyremote can use connectivity  options, it works, but it use the internet connection from the phone (and i pay for this,) 
bluetooth don want to works....
anybody can help me?

---

### Post by DarkHam on 2009-05-25
hey people, excuse me, i create a new thread for this here:
[http://start.ubuntuforums.org/showthread.php?p=7344387#post7344387](http://start.ubuntuforums.org/showthread.php?p=7344387#post7344387)
Thanx

---

### Post by tgm4883 on 2009-05-25
When you plug in the receiver, you should be able to do a 'lsusb' and see if you have the old style or new style MCE receiver.

---

### Post by lwhitmore on 2009-07-21
Hello - did any of you have any luck with gAnyremote?

---

