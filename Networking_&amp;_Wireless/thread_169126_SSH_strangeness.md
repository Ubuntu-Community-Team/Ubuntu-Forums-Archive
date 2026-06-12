---
title: "SSH strangeness"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by futz on 2006-05-02
OK, I've got 3 linux boxes here on a network. All three share files with SSH. There is one Breezy box (this one), one Dapper box and one Fedora box. 

Everything worked fine till I replaced the old Dapper box with a new Dapper box on Sunday. Suddenly I can't access the Dapper box from the Ubuntu box, tho I can access it just fine from the Fedora box. The Dapper box can access both other boxes just fine too.

The previous Dapper box had no such problems. I've looked at everything I can think of, but I can't get it to work. Iptables is completely disabled on the Dapper box.

Anybody got any ideas what could be going on? ](*,)

---

### Post by jazzmuzik on 2006-05-02
This is what I do.

1. Edit the file ~/.ssh/known_hosts

2. Delete the entry of the computer that is not responding. Save and exit.

3. Try ssh again and it should ask you if you want to allow the remote box to connect. Say yes and it will write a new key to that file.

4. Should work at that point.

---

### Post by futz on 2006-05-02
Thank you jazzmuzik! The file is encrypted or something - just gibberish, so I just cleared it all. And now I can SSH to my Dapper box again. 

Guess it must store the mac address or some other identification like that in there, and when I changed boxes, but not IP addresses, it choked?

---

### Post by jazzmuzik on 2006-05-02
ssh uses the known_hosts file to store keys. When you try to connect, if those keys don't match it won't allow connection. The problem was you upgraded your Dapper box, but the known_hosts file had a key for the old Dapper box. Thus there was a mismatch and ssh refused to recognize the new box. It's a security thing. You have to remove the old key and confirm that the new box is okay to connect to. By deleting the old key as I showed you and then rerunning ssh you confirm the new box and a new key is saved. You'll be good until the next time you do anything that changes the values stored in known_hosts.

---

### Post by Slim Odds on 2006-05-02
futz, what method do you use to connect using ssh?

Because you should have seen a prompt telling you that remote key didn't match. That would have been your hint to look at the known_hosts file.

---

### Post by futz on 2006-05-02
[QUOTE=Slim Odds]futz, what method do you use to connect using ssh?

Because you should have seen a prompt telling you that remote key didn't match. That would have been your hint to look at the known_hosts file.[/QUOTE]
Hmm... I saw no such prompt. It just said it couldn't connect. I forget the exact wording.

I use Places/Connect to Server to set up "shortcuts" to the other boxes. Then they show up in Nautilus and I can just treat em like another drive (or drives).

---

### Post by Slim Odds on 2006-05-03
[QUOTE=futz]Hmm... I saw no such prompt. It just said it couldn't connect. I forget the exact wording.

I use Places/Connect to Server to set up "shortcuts" to the other boxes. Then they show up in Nautilus and I can just treat em like another drive (or drives).[/QUOTE]

Sounds like it probably sent that message to a log file. Check /var/log/

---

### Post by futz on 2006-05-04
[QUOTE=Slim Odds]Sounds like it probably sent that message to a log file. Check /var/log/[/QUOTE]
Ummm... There's a hell of a lot of log files in there. Any specific one I should be looking for? There's nothing there with ssh in the title anyway.

---

### Post by Slim Odds on 2006-05-05
[QUOTE=futz]Ummm... There's a hell of a lot of log files in there. Any specific one I should be looking for? There's nothing there with ssh in the title anyway.[/QUOTE]

I think that it would be in auth.log

---

### Post by neouser99 on 2006-05-05
when running into ssh problems, use the -v flag for ssh, it would have told you that there was a possible middle man attack becaues the keys changed therefore not letting you log in.
```
ssh -v <user>@<server>
```

-neo

---

### Post by .dm on 2006-05-16
Im having similar problem actually. Connecting to ssh server from gnome ui then logging in works. But then command line ssh clinet starts to complain about known_host fingerprint not matching. when i remove the offending line and connect via command line the gnome network mapping stops working (im assuming the fingerprint doesnt match the known_host file, because as soon as i remove it it works again).

Could there be a problem with gnome-vfs or whatever is on the backend generating a different fingerprint to command line ssh utlity? 

.dm

---

