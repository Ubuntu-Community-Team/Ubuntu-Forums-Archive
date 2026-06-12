---
title: "Throughput Testing"
date: 2009-06-25
forum: Networking &amp; Wireless
---

### Post by BeauRoch on 2009-06-25
I have setup a lab environment whereby I have two laptops running Ubuntu 9.04 with 100Mb links into their own lans.  Those lans are connected to Cisco routers (2800s) that have a GRE/IPSEC tunnel built between them. Ping rates are 1-2ms between laptops.
I am trying to show throughput comparisons with different OSs.  I have run tests using Win XP Pro and Windows 7 (RC1) and now I am onto Ubuntu.
I have been transferring three files between the laptops (115MB, 512MB and 1GB).  I was expecting the linux systems to blow away the Windows systems but that has not been the case so far.  I have tried xfers using "rcp" and "rsync".  RSYNC has avg. rates of 35Mb/sec while RCP has been around 42Mb/sec. For comparison, Win XP Pro was around 32Mb/sec and Win 7 was around 40Mb/sec.
I have worked with Cisco and my tunnel is running at its optimal level.
Are there other options I should be trying to get better xfers speeds?  I am wondering if SSH is what is slowing me down.

---

### Post by jhannah on 2009-06-25
The overhead of SSH is generally offset by the compression it offers. Are you using SSH with rsync as well? You might be able to get more performance out of the machines by changing some of the TCP tuning options in /etc/sysctl.conf such as the ones below:

```

net.core.rmem_max=8388608
net.core.wmem_max=8388608
net.core.rmem_default=65535
net.core.wmem_default=65535
net.ipv4.tcp_mem=8388608 8388608 8388608
net.ipv4.tcp_rmem=4096 87380 8388608
net.ipv4.tcp_wmem=4096 87380 8388608

```

Provided they are somewhat modern machines those settings should give you better networking performance all around. Just run 'sudo sysctl -p' to apply the changes.

If that doesn't give you a clear boost in speed, I would recommend trying your test w/o the 2800s and simply cable them together with a switch. That will rule out any issues on the testing hosts.

Let me know if that helps.

---

### Post by BeauRoch on 2009-06-25
Thanks Jon - I will give that a shot.
Part of my testing results will include a "LAN" portion whereby I will connect the laptops on the same switch within the same subnet.  Just wanted to do everything I could through the tunnels first before reconfiguring the laptop's network interfaces.
I will reply with results once I have applied your suggestions.

---

### Post by BeauRoch on 2009-06-25
Just finished and those changes did not improve throughput at all through the tunnel.
Is it safe to say that using rcp and rsync are probably my best file transfer options between ubuntu systems over a "wan"?

---

### Post by timcredible on 2009-06-25
windows used to have a pretty lame ip stack, but it's not bad anymore.  speeds are about the same anymore for file transfer.

---

### Post by jonobr on 2009-06-25
Hello

I would recommend using iperf for testing between the clients.

Getting the syntax is tricky but, once you get it right and your testing the right amount of data in each payload, if offers useful information
You can also test upload and download traffic based on UDP and TCP.

I think it also moves away from application issues where scp may have additional encryption which may fudge results etc.

In [THIS]("http://ubuntuforums.org/showthread.php?t=1184075&highlight=iperf")
post I mention in there how I use iperf and the commands I use between client and server and how to test with two terminals.


You could also download jperf which is a fancy java based gui frontend,
and nice graphs but Im a cli type person.

One other thing,

when you kick off iperf first, its first few responses appears to skew higher or lower,
the time you test over should be large enough to normalise you data

Hope this helps

jonobr

---

### Post by BeauRoch on 2009-06-29
iperf ran great across the LAN (98Mb/s) while through the GRE/IPSEC tunnel was only 41Mb/s.

rsync got to the low 70's (Mb/s) across a LAN and mid to high 30's (Mb/s) across the tunnel.

rsync got to the low 90's (Mb/s) across a LAN and low 40's (Mb/s) across the tunnel.

All this has proven that WinXp is slow and that Win7 will be very comparable to any linux setup when it comes to comparing file transfer rates.

---

### Post by jonobr on 2009-06-29
Excellent, thanks for the post back, that was good of you to provide your info back.

Im wondering on the iperf piece of the test.

Given what your test shows, it appears that the addition of the GRE headers in the tunneling do have a significant impact on the throughput?

WOuld that be a fair assessment or would you think its the encapsulation /decapsulation which takes the time?

I think part two would be negligible, but am interested on your thoughts/experience

---

### Post by BeauRoch on 2009-06-29
It is hard for me to determine that right now but I can test that angle by rebuilding my tunnel as a GRE and then IPSEC and re-run the tests through them.  That may shed light on which is causing more problems.  I would have guessed the GRE since IPSEC tunneling is usually more of a CPU hog and my CPU utilization on my C2800s has been low.  I actually had to swap out my C2651XMs because the CPU spikes during transfers were causing a negative impact on my results.
Once I complete my new set of tests I will post those results.

---

### Post by BeauRoch on 2009-06-30
This latest testing showed the difference while running tests through a GRE tunnel vs. IPSEC tunnel

**_Tool_**   **_Tunnel_**   **_Results_**
iperf            GRE         low 50s (Mb/s)
iperf            IPSEC       low 40s (Mb/s)
rsync            GRE         low-mid 40s (Mb/s)
rsync            IPSEC       mid-upper 30s (Mb/s)
rcp              GRE         low 50s (Mb/s)
rcp              IPSEC       low 40s (Mb/s)

This clearly showed that the encaps/decaps do have an impact in the testing results.  Throughput through GRE tunneling  was noticeably better.
The next testing that I think I want to do is take my WAN link down from 100Mb to 10Mb and see if that proportionally impacts my results.

---

### Post by jonobr on 2009-06-30
Excellent information,

Thanks for sharing!!!

:guitar:

---

