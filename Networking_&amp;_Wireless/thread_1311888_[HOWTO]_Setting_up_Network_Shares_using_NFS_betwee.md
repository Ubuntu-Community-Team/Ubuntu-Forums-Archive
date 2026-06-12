---
title: "[HOWTO] Setting up Network Shares using NFS between 2 Ubuntu computers."
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by whiskeyfrances on 2009-11-02
First of all, allow me to state that **I am in no way an expert in this topic (or any other in particular)**.  Please, if you read this and you know how to set up a GUI for this, do so... Many people will thank you (me included).  *And by all means, if there's a simpler way, please let me know.* :)

Now, in my case, I wanted to upgrade to the newest version of Ubuntu, but I need to back up all that I have on my laptop first.  By far the easiest way should be setting up an NFS share and just mounting it on my desktop computer to copy the files.  Here's the result in hopes that it might help you (and me, just in case i forget :D).

This is a merger of two guides I used, which can be found at:
[http://clararaubertas.net/blog/share-folders-between-two-ubuntu-computers-on-the-same-lan-with-nfs/]("http://clararaubertas.net/blog/share-folders-between-two-ubuntu-computers-on-the-same-lan-with-nfs/")
[http://ubuntuforums.org/showthread.php?t=444691]("http://ubuntuforums.org/showthread.php?t=444691")


On the client:

1. In a Terminal window, run

```
sudo apt-get install nfs-common
```

— this installs the software you’ll need.

2. Run

```
ifconfig
```

to find your IP on the local network; it should look something like

```
inet addr:192.168.1.101
```

(If you see more than one instance of “inet addr” in the output of ifconfig, choose the address that doesn’t begin with 127.)

On the server:

3. In a Terminal window (*Alt + F2 and write gnome-terminal then press enter*), run

```
sudo apt-get install nfs-kernel-server
```

4. Edit the /etc/hosts file by issuing on a terminal this:

```
sudo gedit /etc/hosts
```

and add a line that looks like this:

```
192.168.1.101 neuron
```

where “neuron” is replaced with the *hostname* or a nickname for your client (in this case, “neuron” is the name of my laptop) and “192.168.1.101&#8243; is replaced with the *IP* you found in *step 2*.

5. To test this in a Terminal, run

```
ping -c 1 neuron
```

(or whatever name you used) and see if you get a response. If you get a response like “unknown host”, something is wrong — re-check your work from the previous steps (and check that the two computers are really on the same network!). 

If you get a response like “… 64 bytes from neuron… 1 packets transmitted, 1 received … ” then everything is hunky-dory so far and you are ready to move on!

BE CAREFUL: If you use OpenDNS (I know I do) you could get a false positive for your test, check it twice to see if it's called neuron (in my case, whatever you put there in yours) and **not** something like neuron.ispaddress.com

6. Edit the /etc/hosts.allow file

```
sudo gedit /etc/hosts.allow
```

and add a line that looks like this:

```
ALL: 192.168.1.101
```

(again, use the IP that you found in Step 2).

7. To export a file system, you use the exportfs command. This command gives "boffin" access to a file directory and all directories below:

```
sudo exportfs boffin:/home/music/
```

You can run this multiple times to export more than one directory (*this will need you to set up multiple mounts on the other PC*).

The default is to export file systems as "read-only". You can change this by running this command instead:

```
sudo exportfs -o rw boffin:/home/music/
```

To see information about exported file-systems and test what you've done, run this command:

```
exportfs -v
```

And if you want to change options, you sometimes want to first un-export a file system and then re-export it, so the command may be something like this:

```
sudo exportfs -u boffin:/home/music/
```

Where “boffin” is replaced with the hostname/nickname of your server (”boffin” is the name of my desktop) and "/home/music/" is replaced by the actual path you want to share. 

8. Run

```
sudo /etc/init.d/nfs-kernel-server restart
```

to restart the nfs server so it catches up with your changes.

9. Run

```
ifconfig
```

and get the IP of your server, the same way that you found it for the client.

Back on the client!

10. Edit the /etc/hosts file

```
sudo gedit /etc/hosts
```

and add a line like

```
boffin 192.168.1.103
```

where “192.168.1.103&#8243; is replaced with the IP of your server (*from step 9*) and “boffin” is replaced with the *hostname/nickname* of your server (”boffin” is the name of my desktop).

11. Lets test it by pinging from a Terminal

```
ping -c 1 boffin
```

to check that this worked, just like in Step 5.

12. Make a *mountpoint* for your *shared directory* — in my case, I used

```
mkdir /media/boffin-music
```

13. Mount the shared directory at the *mountpoint*, like this:

```
sudo mount -t nfs boffin:/home/music /media/boffin-music
```

replacing “boffin” with your *server’s name*, “/home/music” with the location on the server of your *shared directory*, and “/media/boffin-music” with the *mountpoint* you created in *step 12*.

If it fails by saying it could not mount, restart the nfs-kernel-server by running

```
sudo /etc/init.d/nfs-kernel-server restart
```

and try again the mount in step 13.

And now it works!

If you do all of this on both computers (client and server, replacing the data accordingly) you'll get both shares to be mounted, each one in the other computer.

A cool application of this would be to use "backintime" to backup your work on a server!

No Samba didn't work for me.  And before you say so, yes, it might have been my fault. :P

Hope this helps you :)

---

### Post by Iowan on 2009-11-02
[Another]("http://ubuntuforums.org/showthread.php?t=249889") NFS How-To.

---

### Post by Kat of Zion on 2009-11-04
> **Iowan said:**
> [Another]("http://ubuntuforums.org/showthread.php?t=249889") NFS How-To.

So far, I have encountered a couple of problems in my attempt.

1. The NFS kernel daemon seems to hang when it comes to starting (running the restart command).  

2. Im still unable to use mount /var/www without lacking any result.   Says that the fstab or mtab file doesnt list it, but thats not true.  I did add it to both to make sure it finds it in one of these two, but to no avail.

---

