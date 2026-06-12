---
title: "Issue with media sharing and Windows"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by datpapi on 2010-03-08
Hi guys,
 
Forgive me if this is covered already or mis-threaded. I've searched the forums but am unable to find any real topics covering this. 
 
I am having issues with streaming media(music and movies), well just transfer speeds period, from my Windows Vista desktop PC and my Ubuntu laptop
 
On my Windows PC I have two folders shared: Music and Movies. I also have Media sharing enabled on my Windows PC so that I can stream my music and movies to my Xbox360 and playstation 3. My game consoles have no issues at all with playback speed and quality. My laptop is a dual boot with Windows and Ubuntu. 
 
Streaming to my laptop under Windows is fine. Playback is great and copying files to and from my network shares(Music and Movies folders) is fast.
 
However, under Ubuntu, I've mounted an SMB share to the Windows computer to each folder. When I browse to an MP3 song in VLC, I cannot even listen to it! It'll constantly buffer every few seconds. Forget about trying to watch a movie in VLC either! XBMC and Boxee are useless because they NEVER finish scanning the network folders to even add my content - let alone try to stream them.
 
Trying to copy 89MB (an album worth of MP3s) from the Windows server to Ubuntu was going to take 8hours!
 
Something is definitely wrong here and I just can't figure it out. Should I be connecting to Windows using some other networking method besides SMB?
 
My network is setup with my Windows Desktop connected via 100MB ethernet to a wireless router. The Router is dual broadcasting in G and N modes. I have excellent connection strength and full network rate (54MB for G) on my laptop. Again, networking is fine when using Windows on the laptop.

---

### Post by Iowan on 2010-03-08
As I recall, there's something in [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To about slow Samba shares working better when mounted via FSTAB.

---

### Post by datpapi on 2010-03-11
> **Iowan said:**
> As I recall, there's something in [this]("http://ubuntuforums.org/showthread.php?t=288534") How-To about slow Samba shares working better when mounted via FSTAB.
 
Strangest thing happened last night. For some VERY odd reason everything worked right! Initially when I went to PLACES - Network and attempted to browse my Windows network, I got an error message. This was in addition to the speed problem mentioned above. 
 
Last night Ubuntu suddenly decided it wanted to place nice and show all my Windows PCs when browsing Places-Network and I could mount Samba shares to my Windows Shared folders. 
 
The copying and streaming quality was on par with my Win7 install on this same laptop. 
 
While I'll take this fluke fix, I would really love to understand what the heck happened to fix this. Though new to Linux, I'm very well versed in the world of M$ and would be able to determine the root cause. I just hate not knowing enough about linux to do the same.

---

### Post by datpapi on 2010-03-14
Ok, I guess I spoke too soon. 

Wondering if anyone could provide assistance with Ubuntu 9.10 sometimes wanting to browse my Windows network and other times not.

I can't really provide any real reasoning for this. I can boot into Ubuntu one time, got to PLACES - Network and see all my Windows based computers and browse their shared folders. THEN I can shutdown, startup Ubuntu later and not see a thing! Should I double click the Windows Network Icon, I get ERROR: Unable to Mount Location. Failed to retrieve share list from server

I may get this a few times and then one time boot into Ubuntu and everything magically works again!

The network is functioning properly on my Ubuntu laptop - I can browse the internet and use smb:// to manually map to my Windows Server computer and from there browse all shared folders. Help?

---

