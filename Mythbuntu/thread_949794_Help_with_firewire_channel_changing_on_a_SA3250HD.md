---
title: "Help with firewire channel changing on a SA3250HD"
date: 2008-10-16
forum: Mythbuntu
---

### Post by sgtstadanko on 2008-10-16
Hey All,

Trying to get the sa3250hd channel changing via firewire and contrib scripts going and having no luck.  I know myth has builtin support for this now but I need to use an external script since I am calling it to change the channel on my PVR-150 and the internal one only works if you are using the firewire to capture video. The communications are all correct so not sure why it isnt working. Here is the status:

firewire_test -p -n 0 -r 5 says:

```
Action: Test P2P connection 5 times, node 0, channel 0
P2P: Testing...Success, 31 packets received
P2P: Testing...Success, 73 packets received
P2P: Testing...Success, 39 packets received
P2P: Testing...Success, 79 packets received
P2P: Testing...Success, 29 packets received

```



I am able to tune to a non-encrypted channel with the remote and run test-mpeg2 > hdfile.mpg and play the captured hd stream in mplayer.

plugreport says:

```
Host Adapter 0
==============

Node 0 GUID 0x00169214a03c0000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=1
	channel=0, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

Node 1 GUID 0x0011066645557289
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR
```


So that looks good.  I have tried the following channel changers/primers..
sa3250ch from contrib, sa4200ch from old cvs ticket, sa4250_ch found here, mythprime.98.a.  None of them work.  I have made sure that my model and vendor ID are included in the code as sa3250ch -v says:

```
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
```

So basically I am clueless as to why its not working.  Any ideas?

Thanks

---

### Post by newlinux on 2008-10-16
what happens when you run the channel changing script commandline to change a channel? What error are you getting?

---

### Post by sgtstadanko on 2008-10-16
No errors.  Here is the output from the changers i have used:

```


 sa3250ch -v -s 650
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
Using single number channel change command method
AV/C Command: cmd0=0x00487ce7 cmd1=0x04028a00 cmd2=0x00000000

sa3250ch -v 650
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
AV/C Command: 650 = cmd0=0x00487ce7 cmd2=0x04303536 cmd3=0xff000000
AV/C Command: 650 = cmd0=0x00487c67 cmd2=0x04363530 cmd3=0xff000000

./sa4200ch -v 650
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
AV/C Command: 11214 = cmd0=0x00487ce7 cmd1=0x04028a00 cmd2=0xff000000 cmd3=0x00487c67

./sa4250_ch -v 650
node 0: vendor_id = 0x00001692 model_id = 0x00000be0
Device acquired on node 0
Changing channel 650
AV/C Command: cmd0=0x00487ce7 cmd1=0x04028a00 cmd2=0xff000000

```

None of which results in a successful channel change.  I have tried different unencrypted channels as well with the same results.

---

### Post by sgtstadanko on 2008-10-16
have also tried rebooting and swapping ports on the sa3250.  no dice.

anyone that has got this working and can share that would help.

thanks

---

### Post by majoridiot on 2008-10-17
> **sgtstadanko said:**
> have also tried rebooting and swapping ports on the sa3250.  no dice.

anyone that has got this working and can share that would help.

thanks

try downloading and testing the latest update of mythprime from here: [https://wiki.ubuntu.com/majoridiot?action=AttachFile&do=get&target=mythprime.69c.beta.tar](https://wiki.ubuntu.com/majoridiot?action=AttachFile&do=get&target=mythprime.69c.beta.tar)

compile it with *make clean* and *make*, per the readme, then try running it from the command line (from inside the
compile directory ;)):

```
$ ./mythprime -c 650
```

which will attempt the channel change to 650 before priming.  if that does not work, try forcing the
other SA changers one at a time using the **-f** option, using values 2, 3 and 4.  e.g.:

```
$ ./mythprime -c 650 -f 2
```

one of the three changer should work. once you determine which one does, post a copy of the changer
source you are using and we can patch it up for you.

---

### Post by sgtstadanko on 2008-10-17
Thanks!

Tried channel changers 1-6 (tried 6 for the hell of it but it hung up of course). 

No channel changes, no errors.  I am caputuring with test-mpeg2 > hdfile.mpg and viewing with mplayer.

what baffles me is that capture works but not changing.

I also tried to test myth's internal channel changer.  Setup the FW card as capture and tried defining the model as each of the three SA cable boxes.  No channel change there either...beginning to wonder if there is some kind of firmware issue on the box.

---

### Post by majoridiot on 2008-10-17
> **sgtstadanko said:**
> ...beginning to wonder if there is some kind of firmware issue on the box.

this is your likely culprit.  that is the first SA box that none of the known methods work for.
most 3250s work with the default changer, but some require a 4250 variant, depending on the
firmware.  

a workaround until you can find a fix is to use the irblaster on your pvr-150 to change 
the channels.

---

### Post by sgtstadanko on 2008-10-17
will the irblaster work with the 3250?  i have a mce usb blaster but was under the impression that LIRC would not change channels of the 3250.  I tried to get this working a few years ago and at the time no one had lirc working with a 3250.

update...lirc works.  i was able to send raw commands....now to hack a script.  still sucks about fw.  when i had that working a few years ago it was awesome...way faster.

---

### Post by majoridiot on 2008-10-17
> **sgtstadanko said:**
> will the irblaster work with the 3250?  i have a mce usb blaster but was under the impression that LIRC would not change channels of the 3250.  I tried to get this working a few years ago and at the time no one had lirc working with a 3250.

follow the mythbuntu install guide... [http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.04_installation.pdf)

lirc info begins on p. 111. specifics for the pvr-150 on p. 113. ;)

i'm pretty sure you want to use codeset 78 for for SA3250HD...

---

### Post by sgtstadanko on 2008-10-17
Got it working using the SAE8000 config.


Thanks for all your help everyone.

---

