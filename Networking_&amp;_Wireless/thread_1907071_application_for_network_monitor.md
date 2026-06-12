---
title: "application for network monitor"
date: 2012-01-10
forum: Networking &amp; Wireless
---

### Post by Georgescu1 on 2012-01-10
I want a simple application that allows me to see the ip of someone from Pidgin/Kopete etc that i am speaking with at that moment
I know Wireshark is good but it's to complex for me.

---

### Post by jonobr on 2012-01-10
Hello

Not a solution , but responding as you mentioned wireshark.

Just from an IP level, Im pretty sure (open to correction) the packets when you trace them, dont actually come from the client sending the message.
If your signed up via pidgin to MSN or AIM or IRC etc, the packets will come from another location such as the AIM or MSN service not from the sending user.

So a packet capture wouldnt work for you.

---

### Post by Dangertux on 2012-01-10
> **jonobr said:**
> Hello

Not a solution , but responding as you mentioned wireshark.

Just from an IP level, Im pretty sure (open to correction) the packets when you trace them, dont actually come from the client sending the message.
If your signed up via pidgin to MSN or AIM or IRC etc, the packets will come from another location such as the AIM or MSN service not from the sending user.

So a packet capture wouldnt work for you.

This is true, the only case this wouldn't be true is if you created a "direct" connection for file transfer to the person on the other end of the conversation.

Why do you want to see this btw?  It's completely pointless.

Hope this helps.

---

### Post by Georgescu1 on 2012-01-11
to see if the same person uses 2 different accounts in the same time

I knew on windows using netstat -an or -b had about 20% of showing the ip of the person by just talking to him(I have tested that with a friend after telling him to give me his ip)

with wireshark it just shows me yahoo ip

---

