---
title: "Script to check network availability before mounting NFS"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by snappy46 on 2010-03-13
Sorry if this post does not belong here and not necessarily related to Ubuntu only.

Here's my problem.  I am trying to connect an NFS shared to my multimedia Box.  I have no problem connecting it manually but when I tried to connect automatically upon booting up the multimedia I have to wait for the wireless to be connected before attempting to mount the NFS file system on the media box.

Now I am sure that this can be easily implemented using a script however I do not have much experience with that.  So here my thought process:

1) Mkdir -p /tmp/mnt
2) Create a loop until timeout =20.
    &if ping "location to the file server" return connection is alive
               mount -t nfs :fileserver /tmp/mnt
     &else timeout = timeout + 1  * way out if not available after a certain time
   &endif

I am not sure about the syntax for the loop statement.  I  know what is required for the mount and other stuff.  Is the use of the ping a good idea.  It takes about 2 second for the ping to return when fails so after 40 to 60 sec it should stop.

Thanks

---

### Post by lloyd_b on 2010-03-14
'ping' is exactly the right tool for the job, since it sets it's return value based on whether or not it received a response.

Here's a simple script that I think does what you want:```
#!/bin/bash

# Set timeout to the number of times you want the loop to repeat
TIMEOUT=20

# Create the mount point directory
mkdir /tmp/mnt

# While we haven't used up all the attempts
while [ $TIMEOUT -gt 0 ]; do
    # this will be true if 'ping' gets a response
    if ping -c 1 -W 1 [COLOR="Red"]192.168.0.2[/COLOR] > /dev/null ; then
        mount -t nfs :fileserver /tmp/mnt
        echo "NFS mounted"
        TIMEOUT=0
    # and if there's no response...
    else
        sleep 1
        TIMEOUT=$((TIMEOUT - 1))
        if [ $TIMEOUT -eq 0 ]; then
            echo "NFS Failed to mount - no response to server pings"
        fi
    fi
done
```Note the IP address I have in red - you'll need to replace that with the IP address or machine name for the fileserver (Is it "fileserver"?  I'm not familiar with mounting NFS shares, so I'm just guessing that that is the machine name).

Lloyd B.

---

### Post by snappy46 on 2010-03-14
Thank you very much; this is exactly what I was looking for.  I am slowly learning the shell language; so many things so little time.

Works as advertised except for a few changes that I had to make because of the primitive output given by the media player ping command (busybox).  It returns a "<ip Address> is alive!" string when successful. So I just modified the "if" line to if ["$(ping 192.168.0.100)" = "192.168.0.100 is alive!" ]; then ...  Also it takes about 2 to 3 Seconds for the ping command to return a "<ip Address> not found" so I did not need the sleep command.

Thanks again

PS: can't wait for the next LTS version of Ubuntu.  Ubuntu has been my operating system for the past 3 to 4 years; I think it was 6.01 then or something like that.  I have upgraded since to all the new versions but this time I will try a fresh install; I think I am overdue.

---

