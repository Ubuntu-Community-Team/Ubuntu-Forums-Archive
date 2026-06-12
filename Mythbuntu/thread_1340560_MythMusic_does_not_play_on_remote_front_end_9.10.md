---
title: "MythMusic does not play on remote front end 9.10"
date: 2009-11-28
forum: Mythbuntu
---

### Post by DrJohn999 on 2009-11-28
Using Mythbuntu 9.10 x64 on both machines. No other problems of this nature found thus far. 

MythMusic plays on the main front/backend machine. My remote frontend (only) machine reads and displays the music playlist from the backend but does not play. Setting the remote frontend's music directory to blank, or /var/lib/mythtv/music, or smb://mythtv@<backendserver>/music does not enable playing. The 'Play' triangle control come up highlighted. Pressing 'P' does nothing. The song progress bar does not increment.

Is this a problem with storage groups? I am using storage groups for recordings (the 'recordings' location is blank on the frontend setup, but it finds the videos same as the last scan on the main machine). No so with the music.

-- DJ

---

### Post by movieman on 2009-11-28
Do you have the right codecs installed? I had the same problem today after upgrading and eventually realised that Ubuntu had uninstalled the mp3 codec... reinstalling it and then music played fine.

Of course it would be good if MythMusic actually put up something to say 'I can't play this because I don't have the codec' rather than do nothing at all.

---

### Post by mjezell on 2009-11-28
Had the same problem with basically the same setup as you.  Was pointed to this link by [[COLOR=#76482c]**superm1**[/COLOR]]("http://ubuntuforums.org/member.php?u=44239") on[   [COLOR=Blue]MythTV Wiki[/COLOR] ]("http://www.mythtv.org/wiki/MythVideo")(thanks [[COLOR=#76482c]**superm1**[/COLOR]]("http://ubuntuforums.org/member.php?u=44239")) that explains the problem with storage groups in mythtv v.22.  Mythvideo is the only group that works properly and all others are deprecated until v.23.  I solved my problem by creating a symbolic link to my music files on my fr/be machine
```
ln -s /storage/music /var/lib/mythtv/music
```Then make sure the mythtv group has privileges to the /var/lib/mythtv folder on both the backend and frontend
```
sudo chown -R yourusername:mythtv /var/lib/mythtv
```You will be able to set the path to your music files on the frontend to
```
var/lib/mythtv/music
```I had to use this same process to get my picture files to show up on my frontend too. I also had all my recordings going to storage groups but could not get them to work so all recording are now going to the default group and that works fine. I use NFS to mount the directories from the backend to the frontend and my music and pictures is playing wonderfully in the living room.  Hope this helps.

---

### Post by williammanda on 2009-11-29
I too handle the music & picture directories using NFS for remote FE access. If you need examples using NFS post your reply and I will supply them.

---

### Post by DrJohn999 on 2009-11-29
Movieman:  You were correct -- all the codecs were deleted. I installed them but that did not solve the immediate problem. However, I am able to play music files when the frontend is pointed to music files on the local machine.

mjezell: that didn't quite work for me. Here's what I did:

Shutdown all front/backend processes.

I first relocated the 'music' folder to 'sharedmusic' and then I created a symlink from 'sharedmusic back to 'music' on both machines and set ownership:
```
username@machine:~$ sudo mv /var/mythtv/music /var/mythtv/sharedmusic
username@machine:~$ sudo ln -s /var/mythtv/sharedmusic /var/lib/mythtv/music
username@machine:~$ sudo chown -R username:mythtv /var/lib/mythtv

```

result on the frontend machine (similar on front/backend machine):

```
username@machine:/var/lib/mythtv$ ls -lisa
total 16
3170830 4 drwxr-xr-x  4 username mythtv 4096 2009-11-29 09:49 .
3153924 4 drwxr-xr-x 65 root   root   4096 2009-11-28 09:33 ..
3170657 0 lrwxrwxrwx  1 username mythtv   11 2009-11-29 09:49 music -> sharedmusic
3170860 4 drwxrwsr-x  2 username mythtv 4096 2009-11-29 09:35 sharedmusic

```

Restarted the front/backends. Rescanned for music on the backend machine, which it found. NOte that the backend was still set with storage group music and frontend music folders pointing to '/var/lib/mythtv/music'.

Then I set the frontend path to music as:
```
/var/lib/mythtv/music
```

however no music files were located by scanning for new music (nor did the scanning popup appear). Same if set to the 'sharedmusic' folder, or if left blank. Next, I set the music location to ```
smb://mythtv@backendmachine/music
```
and scanned. This caused some searching activity that never completed. There are about 3,500 tracks in my library, so I left it to search for several hours. This process took about 15 seconds on the backend machine so I'm pretty sure it would never complete on the frontend after this long a wait.

williammanda: yes, please, some examples of nfs share access might be very helpful. The SMB share 'music' is browsable from the frontend machine. NFS is enabled in the control centre.

---

### Post by DrJohn999 on 2009-11-29
I was successful in mounting the nfs share '/var/lib/mythtv/music' from the backend server. To get there:

0. In my case, having moved the music files to another folder and created a symlink to it, I removed the symlink and put the music library back at '/var/lib/mythtv/music'. This corresponds to the default location for music.

1. Enable the NFS service in Myth Control Centre on both the frontend client and on the backend server.

2. On the backend server, edit /etc/exports. Make the music share rw:

```
~$ cat /etc/exports
/var/lib/mythtv/recordings    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/music    *(rw,async,no_root_squash,no_subtree_check)
/var/lib/mythtv/pictures    *(ro,async,no_root_squash,no_subtree_check)

```

3. Update /var/lib/nfs/etab with the change by running (still on the server):
```
sudo exportfs -ra
```

4. On the client, mount the nfs share to the local '/var/lib/mythtv/sharedmusic' folder, which must already have been created:
```
sudo mount mythbuntubackend:/var/lib/mythtv/music /var/lib/mythtv/sharedmusic
```
I have DNS running, so I can use the local name of the backend system. It's also on a fixed IP, so I could use it's IP address too. You could put the music mountpoint anywhere on the client's filesystem. 

List the mounted share to verify that your files are there.

5. Make the mount permanent by editing '/etc/fstab' and adding these lines:
```
#nfs sharedmusic share from MythBuntu backend server
mythbuntubackend:/var/lib/mythtv/music /var/lib/mythtv/sharedmusic nfs rw,hard,intr 0 0

```

Test this by unmounting the share and then automounting it:
```
sudo umount /var/lib/mythtv/sharedmusic
sudo mount -a
```

6. Start mythfrontend, setup the music location to
```
/var/lib/mythtv/sharedmusic
```
and test by scanning for new music. 

7. Restart the client frontend system and observe that the share gets mounted properly on restart.

I may have missed a step in here, so please comment if you like.

---

