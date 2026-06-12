---
title: "capturing data on .pcap file and piping it."
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by gerrybrown on 2011-06-22
Please help! I have a GPS device which sends in data on port number 5000, i am able to capture the data into a pcap file using tcpdump. Now my problem is, i need to pipe the data into a text file as and when data arrives into the pcap file continuously. Can some body help me with a script please?
I did extensive search, but to no avail. been trying to solve this for the past 3 days. 
I use the following commands to capture and pipe the data, but that happens only once when i issue the command. I want this to happen continuously as and when the data arrives. 

tcpdump port 5000 -vvv -w test.pcap

tcpdump -nnr test.pcap > tst.txt

Thanks in advance.

---

### Post by Doug S on 2011-06-23
If you need both the pcap file and the text file, my suggestion would be to run two instances of tcpdump at the same time, one wirting to the pcap file and one writing to the text file.
```
sudo tcpdump port 5000 -w test.pcap
sudo tcpdump port 5000 -nn >tst.txt
```
I usually just do these in two sperate terminal windows, but you could detach them from one terminal and have them run the background (with a "space &" at the end of the command line).

---

