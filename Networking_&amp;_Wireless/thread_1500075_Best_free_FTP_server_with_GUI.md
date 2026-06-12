---
title: "Best free FTP server with GUI?"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by travlemon on 2010-06-02
Hey everyone.

I'm looking to set up a simple FTP server with an Ubuntu 10.04 box that I'm using as a file server.  So far, I've tried a couple FTP server apps from the repos.  One was proftpd with gadmin installed for the GUI.  The other was pure ftp, with PureAdmin installed as the GUI.  

The problem I'm having is that gadmin seems buggy, and PureAdmin I cannot seem to make work properly.  Another dilemma of mine is that I have two large hard drives with several folders  on them.  I only want to share a couple folders from each drive, but have them how up in the home directory of the user that logs in.

It seems like I may need a strong program that supports virtual folders (like Wing FTP), but I wanted to see if anyone out there in the Ubuntu world uses a free one that can help me make folders from different hard drives appear as though they're organized in one home directory?

As mentioned in my heading, I'd prefer something with a GUI.  Thanks in advance!

---

### Post by travlemon on 2010-06-04
> **travlemon said:**
> Hey everyone.

I'm looking to set up a simple FTP server with an Ubuntu 10.04 box that I'm using as a file server.  So far, I've tried a couple FTP server apps from the repos.  One was proftpd with gadmin installed for the GUI.  The other was pure ftp, with PureAdmin installed as the GUI.  

The problem I'm having is that gadmin seems buggy, and PureAdmin I cannot seem to make work properly.  Another dilemma of mine is that I have two large hard drives with several folders  on them.  I only want to share a couple folders from each drive, but have them how up in the home directory of the user that logs in.

It seems like I may need a strong program that supports virtual folders (like Wing FTP), but I wanted to see if anyone out there in the Ubuntu world uses a free one that can help me make folders from different hard drives appear as though they're organized in one home directory?

As mentioned in my heading, I'd prefer something with a GUI.  Thanks in advance!

For reference to those who may read this later: 

I ended up using proftpd with the gadmin GUI tool. I don't have as much freedom as I'd like, but I reorganized some folders and made it work to the best of my liking. 

If you're really looking for virtual paths and all the bells and whistles, Wing FTP server looks like the absolute best there is for Linux.  It is NOT FREE though.  However, if you're willing to dish out the money, it looks like a great solution from what I got from using the demo.

---

### Post by airspoon on 2011-05-27
How are you making out with proftp? Did it ultimately work out for you? I'm in a similar situation, where I'm looking for a good ftp server, though for nothing other than working on a LAMP from Dreamweaver on  Windows and Mac computers.

I have Ubuntu 11.04 Desktop, with Apache2, MySQL and PHP5. I'm mainly using the LAMP only to test dynamic web content before uploading it all to a paid host.

Can anyone recommend a good FTP server for my limited but very specific needs? Thanks.

---

### Post by travlemon on 2011-05-27
> **airspoon said:**
> How are you making out with proftp? Did it ultimately work out for you? I'm in a similar situation, where I'm looking for a good ftp server, though for nothing other than working on a LAMP from Dreamweaver on  Windows and Mac computers.

I have Ubuntu 11.04 Desktop, with Apache2, MySQL and PHP5. I'm mainly using the LAMP only to test dynamic web content before uploading it all to a paid host.

Can anyone recommend a good FTP server for my limited but very specific needs? Thanks.

Hello, I'm doing alright with ProFTP.  Mainly the only thing I am really missing is virtual folders, that's something that you'll only get with a paid ftp server program.  But for simple file sharing, ProFTP is working out for me.

It will be easier to set up with Gadmin-proftp installed.  It's a GUI tool to configure proftp.

You should be able to enter the following command in the terminal to install Gadmin, and it should install proftp for you as well, if you haven't already installed it:

```
sudo apt-get install gadmin-proftpd
```

---

### Post by airspoon on 2011-05-27
Thanks, I'm going to try it.

Edit to add: Hmmmm, apt-get is saying that it can't locate the package.

---

### Post by shaharris on 2011-05-28
Travlemon forgot to add the "d" to the end of ProFTPd...

It is:
```
sudo apt-get install gadmin-proftpd
```

not:

```
sudo apt-get install gadmin-proftp
```

Cheers!

---

### Post by travlemon on 2011-05-29
> **shaharris said:**
> Travlemon forgot to add the "d" to the end of ProFTPd...

It is:
```
sudo apt-get install gadmin-proftpd
```not:

```
sudo apt-get install gadmin-proftp
```Cheers!

Oops, sorry!  I corrected it on my post.

---

### Post by airspoon on 2011-05-29
Thanks guys, I installed it and am running it from inetd. I'm thinking though that I should have installed it as a stand alone server, as it doesn't seem to be working. I did a port scan from a different computer and port 21 isn't showing up. 

If I purge the package, will it also remove itself from the inetd configuration file or will I have to do that manually? Is running it as a stand alone server, easier to configure?

Again, thanks.

---

### Post by airspoon on 2011-06-24
For some reason, I was never able to get proftp to work. When I bring up GADMIN-proftpd, it says: "Status: deactivated" and when I click on the "activate" button, it brings up this error message:
```
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 65 of '/etc/proftpd/proftpd.conf'
```

I'm assuming that I need to purge the package and either reinstall it or install another ftp. I went and bought the "Ubuntu Unleashed" book and it recommends "vsftp". I'm wondering if that may be a better ftp server. Is there any reason why I shouldn't use vsftp or is there a quick-fix for whatever is wrong with the proftpd?

Thanks.

---

### Post by travlemon on 2011-06-24
> **airspoon said:**
> For some reason, I was never able to get proftp to work. When I bring up GADMIN-proftpd, it says: "Status: deactivated" and when I click on the "activate" button, it brings up this error message:
```
 - Fatal: TLSRSACertificateFile: '/etc/gadmin-proftpd/certs/cert.pem' does not exist on line 65 of '/etc/proftpd/proftpd.conf'
```I'm assuming that I need to purge the package and either reinstall it or install another ftp. I went and bought the "Ubuntu Unleashed" book and it recommends "vsftp". I'm wondering if that may be a better ftp server. Is there any reason why I shouldn't use vsftp or is there a quick-fix for whatever is wrong with the proftpd?

Thanks.

Hello,

I didn't notice your post prior to this one.  For your previous post, I don't know enough to give you an answer on that one. Sorry about that!  For VSFTP, the only reason I probably never used it is because it might not have a GUI.

I'm just more of a GUI person, especially when it comes to something a little more complex, like an FTP server.   If you are having trouble with ProFTPd, you can try two things, in regards to your error.

1.  You can try uninstalling ProFTPd in Synaptic, by marking it for complete removal.  Then install it again.

2.  If 1 doesn't work, you can try entering the line, specified in the error, at line 65 of the file that it claims to be missing from.  

Also, I saw you mentioned something about inetd, and that you were running the ftp server through that.  I don't know much about that, as I've only been using Linux for under 2 years.  But, you could try running the server standalone  That's how mine is configured, to run standalone.

I pretty much just install the GADMIN-ProFTPd program, and it took care of everything else with ProFTPd for me.

Sorry it's not much help, but hopefully sheds a little light on the issue for you.

---

