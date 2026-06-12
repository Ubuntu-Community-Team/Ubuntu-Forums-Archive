---
title: "[SOLVED] cannot stream to windows from ubuntu"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by mandrill on 2008-01-07
After having successfully (I think) solved the streaming audio and video from windows to Ubuntu  problem, I now have the reverse issue.
 While windows (XP pro) does manage to do stream, it does not manage to do it well. Lots of stuttering, stops and starts, etc... Music somewhat better than video. I have a GeForce 8400 gs card in xp, 256mb ddr2, and this is on a wireless lan. I use Ubuntu (or want to) as a media server for the xp box - I have a large media collection - and I have not really been able to come up with a solution. VLC on xp didn't cut it, and windows media player is the same - it will play ok for awhile, then stop, then start, with intermediate choppiness, especially on high-action films. 

The over-all connection speed from the network on Ubuntu to windows seems rather slow.Clicking the networked icons in My Network Places are slow to react. I'm wondering if windows has to load a certain amount of data in ram before it can process it, then when it runs out, it fails...

Any ideas, help, or actual solutions will be greatly appreciated, Thanks.

---

### Post by reckless2k2 on 2008-01-07
i could be completely not understanding your situation but your issue sounds like a network problem more than anything. if you are not running gigabit wired between machines, you are going to have multimedia issues especially if you're using wireless. i have gigabit network and media (video and music) is accessed and runs smooth without issue. movies, video, music, etc.. 

as far as music, you may want to make the linux machine a music server and that will fix your music issue with like gnump3d or jinzora. as far as video, you are going to need gigabit network (switch and nics).

---

### Post by mandrill on 2008-01-07
I appreciate your response. As I have no way to hardwire the network right now,  am I to understand from your reply that video must suffer for now? 

However, it looks like you may have offered some hope on the music issue, and I would be happy to hear how to do it.....although not a complete noob, I sometimes need a little more detail than those of you more accomplished than myself.

As always, thanks in advance for help.

---

### Post by archivator on 2008-01-07
How is the streaming accomplished in your case?

I am running a 802.11g network at my house and am able to stream XviD (624x256) with only the slightest sign of choppiness when seeking back and forth. Mind you, that's through 3 layers of concrete. 

I'm currently using sshfs on my Ubuntu to mount the Bitvise WinSSHD-shared Windows drive. SSH is probably an overkill for anyone who doesn't need secure access (but I do). If I had a choice, I would go with a free ftp server on Windows and curlftpfs on Ubuntu. Or Samba (but that seems like the harder way to do it).

---

### Post by mandrill on 2008-01-07
> **archivator said:**
> How is the streaming accomplished in your case?

I am running a 802.11g network at my house and am able to stream XviD (624x256) with only the slightest sign of choppiness when seeking back and forth. Mind you, that's through 3 layers of concrete. 

I'm currently using sshfs on my Ubuntu to mount the Bitvise WinSSHD-shared Windows drive. SSH is probably an overkill for anyone who doesn't need secure access (but I do). If I had a choice, I would go with a free ftp server on Windows and curlftpfs on Ubuntu. Or Samba (but that seems like the harder way to do it).

Streaming thru samba with pyneighborhood from windows to ubuntu. streaming thru (I guess) mshome/samba from ubuntu to windows through a netgear rangemax router. The host machine is an old dell running xp home. the 2 pcs in question both use netgear wpn311 cards.

As for the rest of your response, picture the caveman on the Geico commercials - "Uh, what?"

---

### Post by reckless2k2 on 2008-01-07
gnump3d is very easy to use and will turn you ubuntu box into a streaming media server for internal or external use if you want. i get music to work fine and they claim video but i never got video working right.  probably a query or question or 2 and it would work. 

[http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/)

that link should help you do it all. it's very simple and don't worry about the versions of ubuntu on the top. it works in 7.04 and 7.10 just fine.

---

### Post by mandrill on 2008-01-08
> **reckless2k2 said:**
> gnump3d is very easy to use and will turn you ubuntu box into a streaming media server for internal or external use if you want. i get music to work fine and they claim video but i never got video working right.  probably a query or question or 2 and it would work. 

[http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/28/how-to-setup-gnump3d-for-a-streaming-media-server-ubuntu-510-6061-610/)

that link should help you do it all. it's very simple and don't worry about the versions of ubuntu on the top. it works in 7.04 and 7.10 just fine.

Reckless - thank you for your answer and referral, however gnump3d is not the answer. I am not looking to make ubuntu a media server per se, but I wish to access its media repositories on my media playing machine without delays, stuttering, stalling, etc...in other words, fire up VLC or foobar on windows and enjoy seamless playback from my ubuntu shares. As I mentioned, I currently have succeeded in doing so on ubuntu from windows, but cannot fix (so far) on windows, Thanks again, as always.

---

### Post by archivator on 2008-01-08
Sorry, 'bout the confusion, I thought you needed windows->ubuntu streaming. 

The other way around would be equally simple, actually. You need to install a FTP server on your Ubuntu box (vsftpd is a good starting point, [this](https://help.ubuntu.com/community/FtpServer) is a good guide as well).

Then, all that's left is to use Windows's Network Places (which I've never used) with the risk of some applications not seeing your files. As that could be problematic, you could give [FTP Drive](http://thinkabdul.com/2007/08/06/ftp-drive-free-utility-to-mount-ftp-server-as-local-hard-disk-drive-on-windows-vistaxp-view-ftp-directories-in-folder-structure) a try. It (apparently) mounts remote ftp locations as a local drive, much like curlftpfs. 

I hope this time I didn't make it hard to understand. It's hard to contain my inner talent to overcomplicate things. ;)

---

