---
title: "New type of AIM packet?"
date: 2010-06-18
forum: Networking &amp; Wireless
---

### Post by googlegot on 2010-06-18
My daughter has gotten a new mac and no longer uses our desktop (which had an aim logger installed) to talk on aim.

Now, I can't find any good solutions to logging aim on her laptop, and I didn't want to be intrusive, so I've been capturing wireless packets using airodump-ng.

The problem is, when I use wireshark to analyze the .cap, I cannot read the conversation like I used to be able to years ago.  I know I am capturing the packets, I've caught some of my own, and it seems to be a string of about 5-6 packets that get sent with every message.  Each packet is a fairly standard tcp packet with what looks like an encoded or encrypted section of what I believe to be the message text.

I'm no networking guru, and I'm wondering if there is a new aim protocol, or if anyone has a way to decode the message.

Edit: I ended up putting a hub in between my access point and router and just did a vanilla wireshark capture and lo and behold, all the aim messages in plain text.  I still have no idea how to wirelessly capture these packets, but the old standby still works!

---

### Post by jonobr on 2010-06-18
Hello


Im probably a day late and a dollar short, but Im wondering if this is a packet capture size issue?
I know with a tcpdump command , if you dont specify the pack capture size, then it defaults to something around 64bytes.

that means in your statement you need to define something larger , I usually use a -S 1600 to cover all packet sizes.
I think if you define S0 that means no limit on packet size.
A truncated packet will show up in your wireshark as such.

I also think with a direct wireshark trace there is no such default size and it captures the full packet

---

### Post by Madhtr22 on 2010-06-25
> **googlegot said:**
> 

Edit: I ended up putting a hub in between my access point and router and just did a vanilla wireshark capture and lo and behold, all the aim messages in plain text.  I still have no idea how to wirelessly capture these packets, but the old standby still works!

Hi GoogleGot
I am having the same issue. 
Regarding the hub placement; I'm curious to know if you need to Uplink the hub (ie: first port *(from Cable Modem)* and last port *(To Wireless Router*) plus Uplink button then Sniffer PC in available port or just put them in random ports with no uplink?

My issue is that if I don't uplink I won't receive an IP while attached to the hub, then when I uplink I receive and IP and receive packets, but cannot make out the AIM messages.

Anyhow just curious to hear how yours was setup.

Thanks

---

