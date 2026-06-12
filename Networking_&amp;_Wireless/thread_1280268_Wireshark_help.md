---
title: "Wireshark help?"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Crunchy the Headcrab on 2009-10-01
Hey all.  I'm doing an assignment for college.  I need to use wireshark to analyze a tcp session of me uploading a file to a server.  I'm basically done except I need to know on what frame a certain amount of data has been uploaded by.  I can't seem to find a way of correlating how much data has been transferred to what frame I'm looking at.  Can anyone tell me how to do this?  Thanks.

---

### Post by jonobr on 2009-10-02
Hello


Could you explain a bit more on what you want?

Heres a blurb that is me answering based on what I think your looking for, sorry if im off the mark.....

The application data (Im sure your sick of the OSI and layered models by now) pass the data down the stack and at some point its going to be put into segments then packets and then frames,

the frames are sent to the destination which (if using TCP) will acknowledge the sequence and then ask for more.
This is done using the SYN ACK and FIN 
The amout of actual data contain depends on a few factors but with a TCP connection and its up to the transport layer to get the data from one side to the other.

The data tthat is decapsulated is then ordered and put back together for presentation to the application,

What Im trying to say above is that, if I am understanding you right, there is no way to say this chucnk of data in this packet relates to this. You can see some useful information in some packets (such as viewing passwords and usernames as well as commands in an FTP session as well as other simple sessions, but again, for data transfer, I think your going to be hard pressed.
You can view the actual data, but your going to be looking at a whole heap of Hex characters which wont make a lot of sense , your going to have figure out the packet sequences and so on.

---

