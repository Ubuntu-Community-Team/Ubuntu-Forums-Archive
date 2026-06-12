---
title: "how to test remote loop back in bluetooth"
date: 2014-10-24
forum: Mobile Technology Discussions (CLOSED)
---

### Post by samprat on 2014-10-24
[SIZE=3][COLOR=#333333][FONT=Helvetica Neue]I have small in-house device running on linux platform with bluez libraries.  [FONT=arial][/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]I have created a sco connection with ***Jaber Easygo*** device and everything works as expected. I mean I can play music on my linux machine using ***aplay*** and I can successfully hear on jabber. similarly I can record voice from jabber to linux machine using ***arecord***.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**Now I want to do testing using remote loopback**, so that I send packets from Jabber to Linux machine and receive same packet back into Jabber.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]After trying and spending days I couldn't able to crack it, so I am requesting you guys to please give some advice.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][B]Below are the following things I tried.
[/B][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**1) **Load kernel module snd-bt-sco 2) Ran btsco -v -r[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]**o/p : successfully created the link and can play or record music . so far so good**[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][B][I]Now for remote testing
[/I][/B][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]i) open a terminal and type[/FONT][/COLOR]
> hcitool cmd 0x06 0x002 0x02
[COLOR=#333333][FONT=Helvetica Neue]o/p : sometimes
[B][I]HCI Event : 0xff plen 7 CD 03 00 44 00 00 00
[/I][/B][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]***ii***) In another terminal I use hcidump
[/FONT][/COLOR]
> hcidump -X sco -w test_remote_loop_log

[COLOR=#333333][FONT=Helvetica Neue]***iii)*** In another terminal I record so that packest goes from jabber to Linux box
[/FONT][/COLOR]
> arecord -B 1000000 _D plughw:Headset /home/my_place/test_remote_loop_1.wav

[COLOR=#333333][FONT=Helvetica Neue]then I speak something on Jabber and close the above recording
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]iv) Using ***Wireshark*** and filter type ***"bthci_sco"*** all I have noticed is ***Rcvd SCO DATA*** has data in it ( which is obviously expected) example

[I][B]0000 03 31 00 30 bf ff bb ff e4 etc
[/B][/I][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue]But ***Sent SCO DATA*** has no data in it example
[/FONT][/COLOR]
*0000 03 31 00 30  00 00 00  00 00* ..till end

[COLOR=#333333][FONT=Helvetica Neue]Can some please guide me what I am doing wrong

thansk in advance[/FONT][/COLOR][/SIZE]

---

