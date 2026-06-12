---
title: "Internet Restrictions at Work - GNUMP3d no longer works - Totem: &quot;Location not found&quot;"
date: 2008-10-29
forum: Multimedia Software
---

### Post by TMcKSmith on 2008-10-29
I use GNUMP3d on my home server to stream all of my music.  It's been great for the past year being able to stream all of my tunes while at work by just browsing to the URL [http://myservername.com:8888](http://myservername.com:8888)

Yesterday, my place of business sent out an email saying they were upping their internet restrictions.  All of a sudden, I'm having problems with GNUMP3d.  

I can still access my server's site, however when I try to open a .m3u file with Totem to stream, it gives me "An error occured" "Location not found."

Strangely enough, a co-worker who uses GNUMP3d on his home server is having no problems.  Any help would be appreciated.

---

### Post by TMcKSmith on 2008-10-30
bump

---

### Post by TMcKSmith on 2008-11-03
bump

---

### Post by TMcKSmith on 2008-11-05
bump

---

### Post by fargle on 2008-11-05
Find out what ports you can still get out on.  Set up OpenSSHd on your home server and tell it in the sshd_config file to listen on the port.

Then, at work, do:

```
ssh -p <portnum> -l <username> -L8888:127.0.0.1:8888 <internetIP>
```

This will tunnel to your home system via SSH on whatever port you can use and do a port forward to the server running on port 8888 of your home server over the tunnel to your client machine.  Connect to [http://localhost:8888](http://localhost:8888) on your client machine and you should be good.

Of course the easiest thing to do is just consider changing the port number of your home MP3d server to a port that your work allows, but it's probably not a great idea to have the server hanging out on the Internet on a well-known port for all to see in any case.  Best thing to do is use OpenSSHd on a non-standard port (ideally NOT port 22) and use the above command line to tunnel whatever ports you want.

If your work switched to using a proxy, you can use the connect-proxy app to tunnel your SSH connection via the proxy.  If they tightened down that much, you'll likely have to use port 443 on your home system for the proxy to allow you through.

As an added bonus, if you want to get around any content filtering at work, you can run tinyproxy on your home system, forward that port over the SSH tunnel, and set it as your proxy in your browser.  You'll be able to surf at work via your home connection with no content filtering.  Just watch what's on your screen!

---

