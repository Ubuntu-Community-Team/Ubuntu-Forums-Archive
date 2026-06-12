---
title: "Ubuntu 12.04 Bluetooth smartphone problems."
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by valroadie on 2013-06-05
Hello all!

So I have a samsung sch-s720c smartphone. I am also running ubuntu 12.04 on my macbook 2,1 laptop. NOW.

I can connect the devices through bluetooth, BUT only through audio files. 
I'll see if I can provide an example:
[IMG]http://i39.tinypic.com/nfirlw.jpg[/IMG]
Sorry for the contrast but I had to really lower the lighting to make it readable. 

SO, it says connected to phone audio. I am not able to send pictures (which is all I want to do.) I can show a picture of that as well:
[IMG]http://i42.tinypic.com/ef1cl.jpg[/IMG]
As it shows, any time I try to send a pic to my laptop it gives me this. 
There is no prompt which show the phone trying to send, like it should. The prompt that says reject or accept. 

I use the blueman bluetooth manager as well as the one that comes default with the distro. 

Now I am wondering will they conflict with each other? I don't know, I know that the default manager doesn't work just by itself which is why I installed the blueman. 

SO! Haha can anyone help me out or is anyone else having the same problem? 
Let me know if you need more info as well. 
Thanks!

---

### Post by scbingham on 2013-06-06
I had problems with BT between 12.04 & my android phone.

I removed the default BT packages & only use Blueman, as they seemed to conflict.

On my phone (with BT switched on), I switched on FTP Server:

menu>settings>wireless & networks>Bluetooth>Advanced Settings>FTP Server

Under Blueman>Local Services>Transfer  I setup a shared folder & enabled all the FTP options.

Now I can xfer files between my laptop & phone, initiated from either my laptop or phone.

On my phone I use ES File Explorer, which is very easy to use.

Hope this helps.

---

### Post by valroadie on 2013-06-06
Ah great! Thank you. 

Could you maybe explain to me how to remove the default BT packages? I would do it manually but I wouldn't want to mess anything up which is easy to do in synaptic heh. 

That sounds like an idea on the FTP transfer, I will def. try that when I disable the default BT and install blueman back on here. 
I did see a difference from blueman and the default BT manager as only twice have I been able to access my phone through blueman so..

---

### Post by scbingham on 2013-06-07
I did it from within Software Centre, just typed in blue & removed all the installed packages (3 possibly 4), including Blueman.

Then reinstalled Blueman & all was well.

---

### Post by valroadie on 2013-06-12
Thank you for that scbingham!

Though I am still having the same problems after trying that method. 

It seems I can only connect sharing audio...?

It gives me this error when I try to browse files on device: Could not display "obex://[28:98:7B:64:76:C7]/".

So if anyone else has any ideas or is having the same problem, chime in!

---

### Post by scbingham on 2013-06-12
When you click on the BT icon in the notification bar & then select Local Services, you should see Audio, Network & Transfer. Under Transfer I just selected all the options & also chose a shared folder.

---

### Post by scbingham on 2013-06-12
Also check under Plug-ins that TransferService is selected.

---

### Post by valroadie on 2013-06-12
Ah well the thing is, I cannot get wifi on my phone (I believe it is the wireless chip on the inside is messed up) so I could not download that ES File Explorer for my phone. 

SO, I assume the FTP method is out in that aspect, unless you don't need an FTP program on the phone? Idk...

I was able to get a file SENDING but stopped at 7% for about 15 seconds and then failed...my mind is so boggled right now as to why it would do this haha

---

### Post by scbingham on 2013-06-13
You don't have to have that file manager to send/receive files, I only mentioned it because it is easy to use & very useful.
You should still be able to switch FTF on, on your phone. I guess there's an inbuilt FTF app? If not, then you won't have a service on your phone to transfer files & the only service available will be audio.

How do you add apps & install them?

---

### Post by valroadie on 2013-06-16
Well it doesn't have an FTF program, only the default bluetooth hardware it comes with. 

As far as installing apps, I am able to connect to only one wireless point at my local laundrymat haha and I have to be standing REALLY close to the router so...

I am just confused as to why the bluetooth chooses not to work most of the time when SOMETIMES I can send 1 photo...

---

### Post by scbingham on 2013-06-17
[COLOR=#000000]I can only mention this again, as your phone needs to have an ftf service running -

On my phone (with BT switched on), I switched on FTP Server:[/COLOR]

[COLOR=#000000]menu>settings>wireless & networks>Bluetooth>Advanced Settings>FTP Server

or maybe this app could help you (you'll have to do more laundry lol):

[/COLOR][http://www.appsapk.com/bluetooth-transfer-any-file/](http://www.appsapk.com/bluetooth-transfer-any-file/) I've not used this.

---

