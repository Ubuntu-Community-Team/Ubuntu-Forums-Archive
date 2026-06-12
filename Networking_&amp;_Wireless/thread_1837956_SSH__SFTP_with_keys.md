---
title: "SSH / SFTP with keys"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by Gannin on 2011-09-02
I have a server I normally log into with a key file, such as:

```
ssh -i keyfile.pem username@server.com
```

Is there any way to use Gnome's built-in SFTP functionality when using a key file?

---

### Post by papibe on 2011-09-03
I use the command line version of sftp with keys. It is transparent (no options) if you copy and rename your key file to the default location and name:
```
 either ~/.ssh/id_rsa or ~/.ssh/id_dsa 
```
Is this what you are looking for?
Regards.

---

### Post by Gannin on 2011-09-03
It's helpful and it's in the right direction.  Is there some way to graphically get that functionality?  Again, like Gnome's built-in SFTP file browser.

---

### Post by papibe on 2011-09-03
I found [this]("http://principialabs.com/beginning-ssh-on-ubuntu/") guide very helpful. Check the section Public-Key Authentication in order to use the defaults names and location, so you can avoid using the -i option.

Once that is working, both the command line sftp and the GUI interface will use the keys to connect.

Let us know how it goes,
Regards.

---

