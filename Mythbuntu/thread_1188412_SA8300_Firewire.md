---
title: "SA8300 Firewire"
date: 2009-06-15
forum: Mythbuntu
---

### Post by mitchell2345 on 2009-06-15
Hi,

I am running trunk weekly builds.  I just got new cable and am able to successfully record all HD channels from my STV via firewire.  (Yes i know extremely lucky)  

Doing a test with test-mpeg2 -r 1 > file.mpg i get a playable file.

When i add the tuner in Mythtv-setup all is well.  Since the 8300 isnt listed i chose generic.

I then modified the sa3250_ch script to add my ID's and got it working to change channels. I renamed it to sa8300_ch and installed it in /usr/bin.

The issue is everytime i issue a recording i get a blank file of a 5.1kb file.  Event tho firewire-tester and test-mpeg2 work 100% of the time.

I take this as the issue not being my stb but something myth is doing diff than test-mpeg2.

here are some non myth based logs:
```
mitchell@mythtv:~$ plugreport 
Host Adapter 0
==============

Node 0 GUID 0x0011d800018ee05d
------------------------------
libiec61883 error: error reading oMPR
libiec61883 error: error reading iMPR

Node 1 GUID 0x0022cecc76b00000
------------------------------
oMPR n_plugs=1, data_rate=2, bcast_channel=63
oPCR[0] online=1, bcast_connection=0, n_p2p_connections=0
        channel=1, data_rate=1, overhead_id=0, payload=146
iMPR n_plugs=0, data_rate=2

mitchell@mythtv:~$ firewire_tester -n 1 -p -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Dropped 1701052416 packet(s).
Success, 314 packets received
P2P: Testing...Success, 313 packets received
P2P: Testing...Success, 315 packets received
P2P: Testing...Success, 314 packets received
P2P: Testing...Success, 317 packets received
mitchell@mythtv:~$ firewire_tester -n 1 -p -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Success, 314 packets received
P2P: Testing...Success, 312 packets received
P2P: Testing...Success, 314 packets received
P2P: Testing...Success, 316 packets received
P2P: Testing...Success, 315 packets received
mitchell@mythtv:~$ 
mitchell@mythtv:~$ 
mitchell@mythtv:~$ test-mpeg2 -r 1 > test.mpg
libiec61883 warning: Overlayed connection on channel 1.
You may need to manually set the channel on the receiving node.
Starting to receive
^Cdone.
mitchell@mythtv:~$ ls -lh
total 13M
drwxr-xr-x 2 mitchell mitchell 4.0K 2009-06-12 11:13 Desktop
-rw-r--r-- 1 mitchell mitchell 5.8M 2009-06-15 13:33 file.mpg
drwxr-xr-x 4 mitchell mitchell 4.0K 2009-06-14 19:31 firewire
drwxr-xr-x 2 mitchell mitchell 4.0K 2009-06-03 13:00 Music
-rwxr-xr-x 1 mitchell mitchell  16K 2009-06-14 18:37 mythprime.i386
-rw-r--r-- 1 mitchell mitchell 7.2M 2009-06-15 15:50 test.mpg
mitchell@mythtv:~$ 
mitchell@mythtv:~$ 
mitchell@mythtv:~$ sa8300_ch 514
Changing channel 514
mitchell@mythtv:~$ 
mitchell@mythtv:~$ 
mitchell@mythtv:~$ ls -l /dev/raw*
crw-rw---- 1 root mythtv 171, 0 2009-06-15 15:39 /dev/raw1394
mitchell@mythtv:~$ ./mythprime.i386 -v
mythprime .55b beta

Checking for available firewire ports:
Acquiring firewire handle... OK.
1 ports found
Bus reset succeeded

Acquiring handle on port 0.
1 devices detected.  checking avc subtypes...
ERROR reading oPCR0: Invalid argument
Skipping ghost node 0

Attempting to prime device on port 0 node 1.
Powering device on port 0 node 1...successful.
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... Dropped 1877999616 packet(s)...
293 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... Dropped 582221824 packet(s)...
314 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 315 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 316 packets received
Disconnecting P2P connection on node 1, channel 1
Establishing P2P connection on node 1, channel 1... P2P: connection established.
P2P: receiving packets... 314 packets received
Disconnecting P2P connection on node 1, channel 1

successful connections: 5
Successfully primed stb on port 0 node 1.

1 stbs primed, 0 non-stbs ignored and 1 ghost nodes skipped on 1 ports.
mitchell@mythtv:~$ 
```

and when i start a recording:
```
2009-06-15 15:56:09.588 TVRec(5): ASK_RECORDING 5 0 0 0
2009-06-15 15:56:10.013 TVRec(5): Changing from None to Watching RecordingOnly
2009-06-15 15:56:10.016 TVRec(5): HW Tuner: 5->5
2009-06-15 15:56:10.017 FireChan(0022CECC76B00000): Open()
2009-06-15 15:56:10.022 FireChan(0022CECC76B00000): SetChannelByString(665)
2009-06-15 15:56:10.028 External channel change: sa8300_ch 665
2009-06-15 15:56:10.030 Waiting for External Tuning program to exit
Changing channel 665
2009-06-15 15:56:10.068 ret_pid(5427) child(5427) status(0x0)
2009-06-15 15:56:10.069 External Tuning program no longer running
2009-06-15 15:56:10.069 External Tuning program exited with no error
2009-06-15 15:56:10.069 FireChan(0022CECC76B00000): SetChannelByString(665) success
2009-06-15 15:56:10.069 FireChan(0022CECC76B00000): Open()
2009-06-15 15:56:10.094 FireSM(0022CECC76B00000): ctor
2009-06-15 15:56:10.095 SM(0022CECC76B00000)::AddFlags: Seen() Match() Wait(Sig,)
2009-06-15 15:56:10.095 FireDev(0022CECC76B00000): Requesting STB Power State
2009-06-15 15:56:10.096 FireDev(0022CECC76B00000): STB Power State: On
2009-06-15 15:56:10.131 DTVSM(0022CECC76B00000)::SetProgramNumber(1): 
2009-06-15 15:56:10.131 SM(0022CECC76B00000)::RemoveFlags: Seen(PMT,Crypt,) Match(PMT,Crypt,) Wait()
2009-06-15 15:56:10.131 SM(0022CECC76B00000)::AddFlags: Seen() Match() Wait(PMT,)
2009-06-15 15:56:10.131 SM(0022CECC76B00000)::AddFlags: Seen() Match() Wait(PAT,PMT,Pos,)
2009-06-15 15:56:10.131 SM(0022CECC76B00000)::Start: begin
2009-06-15 15:56:10.134 SM(0022CECC76B00000)::Start: end
2009-06-15 15:56:10.157 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-06-15 15:56:10.159 Started recording: Modern Marvels "Logging Tech": channel 3665 on cardid 5, sourceid 3
2009-06-15 15:56:10.165 scheduler: Started recording: Modern Marvels "Logging Tech": channel 3665 on cardid 5, sourceid 3
2009-06-15 15:56:10.134 FireDev(0022CECC76B00000): Requesting STB Power State
2009-06-15 15:56:10.188 FireDev(0022CECC76B00000): STB Power State: On
2009-06-15 15:56:10.188 SM(0022CECC76B00000)::AddFlags: Seen(STB,) Match(STB,) Wait()
2009-06-15 15:56:10.189 FireSM(0022CECC76B00000): UpdateValues() -- Waiting for table monitor to start
2009-06-15 15:56:10.198 FireSM(0022CECC76B00000): UpdateValues() -- Table monitor started
2009-06-15 15:56:10.198 FireSM(0022CECC76B00000): RunTableMonitor(): -- begin
libiec61883 warning: Overlayed connection on channel 1.
You may need to manually set the channel on the receiving node.
2009-06-15 15:56:10.205 LFireDev(0022CECC76B00000): Buffered packets 2000 (8000 KB)

```

when i look at the file it is 0 in size.

now, when mythtv is trying to record the port is still primed and rdy:

```
mitchell@mythtv:~$ firewire_tester -p -n 1 -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Success, 105 packets received
P2P: Testing...Dropped 1713373184 packet(s).
Success, 398 packets received
P2P: Testing...Success, 403 packets received
P2P: Testing...Success, 401 packets received
P2P: Testing...Success, 404 packets received
mitchell@mythtv:~$ 
mitchell@mythtv:~$ firewire_tester -p -n 1 -r 5
Action: Test P2P connection 5 times, node 1, channel 1
P2P: Testing...Success, 401 packets received
P2P: Testing...Success, 402 packets received
P2P: Testing...Success, 400 packets received
P2P: Testing...Success, 403 packets received
P2P: Testing...Success, 404 packets received
mitchell@mythtv:~$ 
```

So what does myth do differently that these other tools?  I just moved from a CentOS build.  Is ther anything i need to do with the firewire stack?  I have tried nearly all combination for what STB i pick in mythtv setup and speeds.

Thanks,
Mitchell

---

### Post by mitchell2345 on 2009-06-16
*bump*

anyone?

---

