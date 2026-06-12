---
title: "getting 4.8MByte/s speed in copying files between computers in lan of speed 100Mbit/s"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by utkarsh009 on 2012-03-22
Hi! I have connected 2 computers having Ubuntu with crossover cable. Connection information shows that the speed is 100 Mbit/s (Mbps) (i think it is equal to 12.5 MByte/s) but when I copy files from one computer to other I get only 4.8 Mbyte/s (MBps) speed. Why?  Does that have anything to do with HDD read/write speed?

---

### Post by ashpuk on 2012-03-23
i am no expert but would suggest you have answered your own question.

hard drive is a factor when you get to these sorts of speeds, as well as the size of files that you are copying. there may also be another bottleneck.

the question is do you need it to be any faster?

if so RAID options are probably worth exploring, but i guess it really depends on what your trying to do?

---

### Post by RyanRahl on 2012-03-23
What protocol are you using to copy? If it is an encrypted protocol like sftp you may be loosing speed due to the overhead involved with encrypting/decrypting

---

### Post by jonobr on 2012-03-23
Hi There


First off


Thanks for opening the new thread.. It really helps people searching for information ):P

On the throughput, yes, what your device puts on the Ethernet will be affected by that, however, just be aware that a byte= 8 bits,
that means a megabyte= 8 megabits,
so 4.8 megabytes = 38.4 megabits per second .

Heres some detail on how ethernet works and explains in part why you will never reach 100mbps.
Also another reason is if your using a slow internet connection (eg a dial up link or slow dsl) then its like suck a large coke through a small straw.

Heres the detail, If you know this already - apologies!

When your computer is not doing anything, its still making a lot of noise on the network and using bandwidth.

If you try doing this 
```
sudo tcpdump -vvv -i any 
```
you will see the packets going back and forth on your Ethernet interface.

The technology that Ethernet uses is called carrier sense multi access collision detect (CSMA/CD).

This means when you start an ftp or ssh session or look at videos on YouTube etc, your computer first looks at the network and tries to sense a carrier. Reason being on a home network connected to a hub, only one machine can talk at any one time. (thats where multi access comes in)
When the device sees no one is using the line, it starts transmitting its data.
If two devices transmit at the same time, there is a collision, like in a conversation. Both parties back off for a random period and then resend.

The more devices on the network the more retransmits and collisions go on.
Although this sounds archaic , it works very well, 
If you put too many devices on the one network though, the network gets overloaded and everything finds it hard talk.
much like an overcrowded room.
This is fixed by breaking a network into multiple collision domains (i.e. adding more switches and placing them strategically in your network.)

In the end although your network and cable support 100mbps it will never actually reach that number because of CSMA/CD.

As also mentioned before, I would ensure running ifconfig you are doing full duplex 100mbps,



Hope this was useful

jonobr

---

### Post by utkarsh009 on 2012-03-23
@Ryan : I use SMB.
@jonobr: thanks I didn't know that. The thread is solved, I guess.

---

### Post by jonobr on 2012-03-23
Hi there


Im hoping I didn't baffle you into submission!!!

If your not sure or you feel there is still a problem, let me (us)  know

---

### Post by utkarsh009 on 2012-03-23
No problem at all. I'm more worried about the fact that sometimes the LAN works fine but sometimes I have to reboot it again in order to ping or access shared folders. I guess 11.10 has some problem with wired connection because it doesn't recognize available connections immediately and may take upto 2-4 minutes but 10.04 LTS recognizes it immediately. But the speed issue is solved as I've seen many threads in which people with 7200 RPM drive speed were getting only upto 11MBps speed at max and I have a 5400RPM drive in my netbook. So I guess that's the bottleneck.

---

### Post by Roasted on 2012-03-23
On a 100 LAN, your absolute max remotely possible is 12.5 MB/s. Factor in a 5400 RPM drive, excessively long runs of ethernet cable, a router that may be somewhat lackluster in quality, and some ceiling lighting being right up against some of the ethernet runs and you'll have significantly diminished throughput.

In a perfect world, if I hit 9 MB/s, it's a good, good day. Typically I average 6-7 on a 100 LAN. Samba is the only protocol I use. At one point I did a direct comparison between NFS and Samba, and it revealed Samba was a tad quicker, which was kind of LOL since some people use NFS believing its superior in speed (yeah okay).

Same scenario as above, except gigabit, I average about 38-40 MB/s.

All of the above is true when I remove Linux from the equation and put Windows in place, which suggests its just the bottleneck of the hardware/networking gear in place.

For fun I might add a Samba share to my desktop which has an SSD and see if the speed changes at all writing to that... hmm...

---

### Post by DeMus on 2012-03-24
Well, using Samba is a whole lot slower than using NFS.
With Samba I get a maximum of 7 MBytes/sec on a 100mbps network, now when using NFS I get 12MBytes/sec which is really close to the 12.5 which is the absolute maximum (100/8=12.5).
Slow disks and slow processors do influence the speed of course.

---

