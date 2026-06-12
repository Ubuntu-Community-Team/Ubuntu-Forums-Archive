---
title: "dsl install disk incompatible with linux"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by spike316 on 2006-03-13
ok i have sbc dsl, hooked up with a usb cable. i just switched from windows xp professional to linux (and i like it a lot better!) the only problem is that the disk to install the dsl is only compatible with windows or mac. i've tried connecting my modem directly to the computer (mine is the secondary computer) and that didn't do anything either. i also went into the networking thing in linux and no windows or anything came up. <_>

---

### Post by Peter41az on 2006-03-13
are you connecting it to your computer via USB?

---

### Post by Peter41az on 2006-03-13
never mind, i just re read that you were. the modem you have should have a lan port on it. if you connect it through that to the lan port on your computer, it should grab an ip addy and go. make sure the network card is active too...

---

### Post by spike316 on 2006-03-13
wait, lan? <_> i don't know what that means. the reason why i can't use a ethernet cable or anything is that i'm the second computer, and the two computers are in two completley different rooms and there's no way that i can directly connect to the modem. and i even brought the modem and everything in there, just to try it and still nothing happened. :/

---

### Post by Peter41az on 2006-03-13
ok maybe im misunderstanding you. the lan port is the port that uses the network cable. can you explain how each computer is connected, is the primary computer using a network cable ? just so i can get a picture here...

---

### Post by spike316 on 2006-03-13
ok, well the main modem is connected through the phoneline, which is connected to the primary computer. then the secondary computer (mine) is connected through an adapter which is also connected to the phoneline.

---

### Post by aysiu on 2006-03-13
Well, it's definitely not an SBC-Ubuntu thing. I have SBC DSL, and I didn't have to do anything to get it working with Ubuntu. Ubuntu detecting the connection without any configuring.

**Edit**: Your setup's quite a bit different from mine. Mine is a router that's connected through the phoneline. Then all the other computers are connected through the router.

---

### Post by spike316 on 2006-03-13
so do you think it might have been a usb thing?

---

### Post by Peter41az on 2006-03-13
this adapter, it directly connects TO the phone line? or through the modem? sorry to be so inquisitive, but i want to give you the right answer. on the back of the modem should be the phone line connector, possibly a jack for an extension phone, then anywhere from 1 to 4 network ports, am i correct?

---

### Post by Peter41az on 2006-03-13
im thinking he has a dsl gateway, and has the second computer connected somewhere other than the lan port....

---

### Post by spike316 on 2006-03-13
yeah, it has a thing on the back of the modem to connect other lines, but the two computers are in completely different areas of the house so i have to use the adapter.

and yes, the adapter connects directly to the phone line. (well with a regular telephone cord but basically the same.)

---

### Post by Princey on 2006-03-13
If I understand carefully, you have your dsl model feeding two computers and you want the Ubuntu comp using the usb interface for a 3rd connection. The USB drivers won't work with Windows as it only has mac and windows drivers. You can either switch the usb to the Windows machine (if one of the other two are Windows), or use a network hub from the dsl router. The router has NAT so it can theoritically connect 255 other computers. That way, the you can connect the Kubuntu/Ubuntu computer via lan (ethernet). I think that's way better than your current set up.

---

### Post by Peter41az on 2006-03-13
im thinking the adapter you speak of is actually a DSL line filter. You need to connect a Cat 5 network cable from the LAN port on the back of the modem/router to the network port on your computer in order for it to function. Am i thinking right, aysiu or misdiagnosing?

---

### Post by spike316 on 2006-03-13
[QUOTE=Princey]If I understand carefully, you have your dsl model feeding two computers and you want the Ubuntu comp using the usb interface for a 3rd connection. The USB drivers won't work with Windows as it only has mac and windows drivers. You can either switch the usb to the Windows machine (if one of the other two are Windows), or use a network hub from the dsl router. The router has NAT so it can theoritically connect 255 other computers. That way, the you can connect the Kubuntu/Ubuntu computer via lan (ethernet). I think that's way better than your current set up.[/QUOTE]
but the problem with that is that i can't have wires running all through my house. :/ they're in completely different areas. and when i did try bringing the modem into my room nothing happened then either. :/ (sidenote: there's two computers. one's my dad's and has windows, which i'm currently on, and the other is mine and has ubuntu.)

---

### Post by aysiu on 2006-03-13
[QUOTE=Peter41az]im thinking the adapter you speak of is actually a DSL line filter. You need to connect a Cat 5 network cable from the LAN port on the back of the modem/router to the network port on your computer in order for it to function. Am i thinking right, aysiu or misdiagnosing?[/QUOTE] You know, honestly, I'm not that knowledgeable about the subject. I just know what works for me and my wife.

We have SBC/Yahoo! DSL, and we did *not* need the installer disk to get it to work.

From our phone jack, we have a regular phone line splitter that splits the phone line into two phone lines.

One line just goes to our phone. The other line goes to a DSL adapter that feeds into the DSL modem.

We then have an ethernet cord that goes from the DSL modem to our wireless/wired router. The wireless feeds to my wife's Mac Powerbook. There are two wired ethernet connections coming out of the router to my two Ubuntu computers--neither of which needed to be configured. Both just used DHCP to auto-configure the connection.

I know what I'm saying probably doesn't help spike316 *directly*. I just know that Ubuntu has no problem with SBC/Yahoo! DSL, and the installer CD is not needed.

---

### Post by Peter41az on 2006-03-13
heres an idea for you. first of all, you will have to make a connection from the network port on back of router/modem to the network port on your computer in your room. But no wires running through house. buy quantity 2 of these:

[http://www.netgear.com/products/details/XE102.php](http://www.netgear.com/products/details/XE102.php)

Plug one into an outlet near your modem. run a short network cable from the box you plugged in to the network port on back of modem/router. take the second box into your room, plug it into the wall. plug a network cable into it. It will connect you. I have this setup running to my basement, and it runs great, and this is a 5000 sf house :)


wired wireless, voila :)

---

### Post by spike316 on 2006-03-13
so after i finish all this should i like... reinstall? or is it just supposed to pick up on it?

---

### Post by Peter41az on 2006-03-13
you dont have to reinstall anything. it will just work. provided you activate your network card on your computer :) just plug them in and go. they are a wireless dream.

---

### Post by spike316 on 2006-03-13
how do i activate my network card on my computer? just go into the network thing under system? and also, if i tell the people at best buy what i want to do they should be able to guide me a bit right? :/

---

### Post by Peter41az on 2006-03-13
yes, and  sure it says its active, if it isnt, click activate then click configure and make sure it says DHCP for addressing.

---

### Post by spike316 on 2006-03-13
ok and the last time that i tried to do that nothing happened. was that just because it didn't detect anything?

---

### Post by Peter41az on 2006-03-13
take note of the model number on that page i sent, and just tell them you need 2 of them. they arent super cheap, but they arent too expensive either.

---

### Post by Peter41az on 2006-03-13
well if you didnt have an active internet connection, it wouldnt have worked.

---

### Post by spike316 on 2006-03-13
ok thanks so much! ^_^_^_^_^_^_^

---

### Post by Peter41az on 2006-03-13
feel free to pm me and let me know what happened, ill be glad to help. Off to bed for me! heh

---

