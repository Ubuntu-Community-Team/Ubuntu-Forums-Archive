---
title: "MythTV in a LAN: no MySQL Connection from Mythbuntu Frontend"
date: 2009-01-06
forum: Mythbuntu
---

### Post by hhl on 2009-01-06
Hi, hopefully someone can help me here. I've tried for 2 days without any success. Here is what I have:

**SERVER:** 
- Fixed IP address: 192.168.0.42
- OS: Ubuntu Linux 7.04
- Tasks: Fileserver (Samba for Windows Clients)
         Internet Router (DSL)
         TV Receiver (Satellite)
         DHCP server
- MythTV Backend: version 0.20.20060828-3
  (runnung since months, functioning)

**CLIENT(S):**
- IP address from DHCP server
- OS: Windows XP (mostly)
- Connections to MythTV recordings:
     via VLC media player
      (accessing the files on the server directly)
      (poor recording listing, 
       no recording management w/o corrupting database,
       no DVD burn option)
     via MS Win Media Player (incl Vista Codec Package)
      (accessing the files on the server directly)
      (poor recording listing, 
       no recording management w/o corrupting database,
       no DVD burn option)
     via MythTV Player
      (fine listing of recordings, but functtionality 
       is slow, LiveTV option is poor, and I don't see
       how to create DVDs from the recordings)

**Mythbuntu story/Problem:**
For a small Mini PC, connected to the plasma TV, I hoped to get a better/more complete solution with a Mythbuntu frontend. 
So I tried to install **8.04** from the Mythbuntu Live CD. Booting the CD worked, but approach to install failed, as Mythbuntu could not mount the CD due to whatever reason.
The workaround came with the new version **8.10**: Having installed Windows XP on the Mini PC, after sliding-in the Mythbuntu 8.10 CD, the Mythbuntu options menu opened, offering the option to install Mythbuntu like a Win application, which I did. I can now choose to run Mythbuntu out from the Boot Menu.
=> PROBLEM: *I do not get beyond step 11 of the configuration, because the test to connect to the MySQL database on my server always fails! I have already tried many many configuration changes on the MySQL server (access rights, new users, rights for the myconverg database) and in the Mythbuntu MySQL access mask ... but with no success at all.*

Is there anyone, who could give this Linux newbie a **step-by-step help**, how to get this system work?
I'm sure, that such help would also be appreciated by others, as almost all of the 1000s of help topics in the Wild consider only Frontend and Backend on the same machine ("localhost").

---

### Post by ian dobson on 2009-01-06
Hi,

I imagine the mysql isn't setup to allow connections from you network. 

Edit
nano /etc/mysql/my.cnf and comment out the line 
bind-address           = 127.0.0.1 
then restart mysql with 
/etc/init.d/mysql restart

That should be enough for the frontend to connect to the backend.

Regards
Ian Dobson

---

### Post by klc5555 on 2009-01-06
> **hhl said:**
> Hi, hopefully someone can help me here. I've tried for 2 days without any success. Here is what I have:

**SERVER:** 
- Fixed IP address: 192.168.0.42
- OS: Ubuntu Linux 7.04
- Tasks: Fileserver (Samba for Windows Clients)
         Internet Router (DSL)
         TV Receiver (Satellite)
         DHCP server
- MythTV Backend: version 0.20.20060828-3
  (runnung since months, functioning)

**CLIENT(S):**
- IP address from DHCP server
- OS: Windows XP (mostly)
- Connections to MythTV recordings:
     via VLC media player
      (accessing the files on the server directly)
      (poor recording listing, 
       no recording management w/o corrupting database,
       no DVD burn option)
     via MS Win Media Player (incl Vista Codec Package)
      (accessing the files on the server directly)
      (poor recording listing, 
       no recording management w/o corrupting database,
       no DVD burn option)
     via MythTV Player
      (fine listing of recordings, but functtionality 
       is slow, LiveTV option is poor, and I don't see
       how to create DVDs from the recordings)

**Mythbuntu story/Problem:**
For a small Mini PC, connected to the plasma TV, I hoped to get a better/more complete solution with a Mythbuntu frontend. 
So I tried to install **8.04** from the Mythbuntu Live CD. Booting the CD worked, but approach to install failed, as Mythbuntu could not mount the CD due to whatever reason.
The workaround came with the new version **8.10**: Having installed Windows XP on the Mini PC, after sliding-in the Mythbuntu 8.10 CD, the Mythbuntu options menu opened, offering the option to install Mythbuntu like a Win application, which I did. I can now choose to run Mythbuntu out from the Boot Menu.
=> PROBLEM: *I do not get beyond step 11 of the configuration, because the test to connect to the MySQL database on my server always fails! I have already tried many many configuration changes on the MySQL server (access rights, new users, rights for the myconverg database) and in the Mythbuntu MySQL access mask ... but with no success at all.*

Is there anyone, who could give this Linux newbie a **step-by-step help**, how to get this system work?
I'm sure, that such help would also be appreciated by others, as almost all of the 1000s of help topics in the Wild consider only Frontend and Backend on the same machine ("localhost").


The first and primary problem is that Mythbuntu 8.xx doesn't do Mythtv 0.20.2. They're Mythtv 0.21 only. A mismatched slave backend or remote frontend will fail connecting to the server with a protocol mismatch error. 

The last version of Mythbuntu to have 0.20.2 was Mythbuntu 7.10. If you wish to use a live CD or a remote frontend solution with your current Myth server, you can do it with 7.10 on the remote machine. (Don't upgrade the mythtv packages with the 0.21 backports, keep the mythtv 0.20.2 packages)

Alternatively, since AFAIK Mythtv 0.21 was never backported to Ubuntu 7.04, you would need to upgrade your server to at least Mythbuntu 7.10 (with the Mythtv 0.21 backports), or to 8.04 or 8.10 in order to use Mythbuntu 8.x as a remote frontend or a slave backend. An upgrade like that would be dicey and potentially unpleasant, even if the server hardware could handle it.

7.10 is still available out in the wild, if you look for it. Using that on your remote machine would seem to be your more reasonable option.

Cheers! :)

---

### Post by hhl on 2009-01-06
Thank you both for the quick reply!
I commented out the bind to localhost as advised, and I could then test the connection within the Mythbuntu (still 8.10) installation successful, and the installation continues then.
**Next problem:** *(the Mini PC is connected to the LAN via WLAN)*
When rebooting Mythbuntu to complete the installation, the screen with blue background and very big white fond appears, prompting me to enter the connection data again (no Upnp database found). If I do so and confirm, I get the message: [FONT="Courier New"]Cannot login to database?[/FONT]. This is obvious, however, as the computer has no longer any connection to the network. I need to re-enter all and everything (including a very long key) to re-install the WLAN connection.
[COLOR="Red"]How can I make the machine automatically re-connect the WLAN?[/COLOR]

---

### Post by volkswagner on 2009-01-06
> **hhl said:**
> 
[COLOR="Red"]How can I make the machine automatically re-connect the WLAN?[/COLOR]


Not sure after the install, if you set the keyring manager password to the users password, you won't be prompted for it on login.  Don't beat a dead horse, if you don't plan on upgrading the backend, you will have no joy on a .20 and .21 Mythtv protocol mismatch.

At this stage in the game I recommend a fresh install of 7.10 with backports disabled, as suggested by klc5555.  Then you can set the keyring manager password the same as your user password.

---

### Post by hhl on 2009-01-07
re "dead horse" ... I'd like to downgrade to 7.10, but I am unsure how-to. As I mentioned in my initial post, the CD-DVD drive in my mini PC will not be mounted after booting Myth(u)buntu from the CD, and the installation does not work. Or does v. 7.10 also allow installation from within Windows? 
I am grateful for any idea! :D
Thanks for all your help.

---

### Post by klc5555 on 2009-01-07
> **hhl said:**
> re "dead horse" ... I'd like to downgrade to 7.10, but I am unsure how-to. As I mentioned in my initial post, the CD-DVD drive in my mini PC will not be mounted after booting Myth(u)buntu from the CD, and the installation does not work. Or does v. 7.10 also allow installation from within Windows? 
I am grateful for any idea! :D
Thanks for all your help.


Well, the first step is to burn yourself a 7.10 CD, and ascertain that in fact it will not mount your mini-PC's CD. Ubuntu 8.04 introduced at least as many bugs as it fixed, and it is in no way certain without a test that 7.10 will display the same behavior that 8.04 did on that hardware.

Besides, you would need 7.10 anyway in a worst-case scenario to upgrade your server to the minimum level necessary to run Mythtv 0.21 (Mythbuntu 7.10 plus mythtv 0.21 backports) in case your clients end up having to run Mythbuntu 8.xx which is Mythtv 0.21-only.

---

### Post by volkswagner on 2009-01-07
> **hhl said:**
> re "dead horse" ... I'd like to downgrade to 7.10, but I am unsure how-to. As I mentioned in my initial post, the CD-DVD drive in my mini PC will not be mounted after booting Myth(u)buntu from the CD, and the installation does not work. Or does v. 7.10 also allow installation from within Windows? 
I am grateful for any idea! :D
Thanks for all your help.

Try downloading 7.10 from a torrent.  I had an issue with 7.10AMD64 version where the iso checksum was fine and the internal cd check tool reported no errors, yet the install would hang at 87%.  The torrent iso installed without incident.

Perhaps providing details on what does not work for 7.10 install can be addressed.

---

