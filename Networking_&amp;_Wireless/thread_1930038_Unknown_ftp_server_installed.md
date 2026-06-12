---
title: "Unknown ftp server installed"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by etiennenoel on 2012-02-23
Hi,

I have an ftp server installed but I don't know which one it is.
I properly **uninstalled** vsftpd and proftpd. 
I also have xampp installed but the ftp server(proftpd) is stopped. 

However, my questioning here, I can still access an ftp server ( by connecting to it even though I know everything is stopped). Is there a way to know all the ftp servers or the installed programs.

Thanks in advance for any clues,

Etienne

---

### Post by etiennenoel on 2012-02-23
what do you mean ?

---

### Post by coffeecat on 2012-02-23
> **etiennenoel said:**
> what do you mean ?

It was a spammer post - now removed.

---

### Post by Lars Noodén on 2012-02-23
> **etiennenoel said:**
> ... Is there a way to know all the ftp servers or the installed programs...

1) If you've been installing packages outside of the package manager, the only way to keep track of what is install would be any notes that you've kept along the way.  For packages that you've installed the normal way (i.e. via the Software Center, Synatpic or apt-get) then you can look in the Ubuntu Software Center.  

xampp is a good crutch for those still on Windows, where it is hard to install and maintain software.  However, on GNU/Linux, it is one of the hardest ways to work.  You end up having to manually manage what the package manager (the Software Center, Synatpic or apt-get) does for you automatically.  So it is easy to end up with out of date packages.  Further, packages like perl are already part of Ubuntu, so you end up with conflicting duplicates.  

My recommendation would be to remove the /opt/lampp directory and its contents and use the official Ubuntu versions of the software instead.  You can use Synaptic, the Software Center or apt-get to install the packages apache2 and php5. Perl comes built in with any version of Ubuntu so it does not need to be installed. MySQL is split into several packages (mysql-server, mysql-client, php5-mysql, libdbd-mysql-perl, etc.) but you won't need them until you start to program your own CMS or install one that someone else has built.

Here is some good reading on installing software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Let the package manager do the work so that you can spend time working with and using the programs.

2) If you have SSH available, then you already have SFTP and should use that instead of [FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  SFTP is secure, FTP is not.  SFTP requires no extra packages, FTP requires an extra FTP daemon to be installed an configured.  etc.  If you don't already have SSH, then you can get it with the package OpenSSH-server.  So don't install FTP and uninstall it if you have it.

3) About the binaries for the rogue FTP daemon you are looking for, you can hunt for the binaries like this:

```

locate ftpd | grep sbin

```

But that won't tell you if they are part of an official package or were installed by hand.  Again, if you installed by hand, check your notes.

You can find out if the file is part of an official package like this:

```

dpkg -S */path/to/some/file*

```

---

### Post by winh8r on 2012-02-23
> **etiennenoel said:**
> Hi,

I have an ftp server installed but I don't know which one it is.
I properly **uninstalled** vsftpd and proftpd. 
I also have xampp installed but the ftp server(proftpd) is stopped. 

However, my questioning here, I can still access an ftp server ( by connecting to it even though I know everything is stopped). Is there a way to know all the ftp servers or the installed programs.

Thanks in advance for any clues,

Etienne

If you open the Synaptic Package Manager and enter ftp in the search box,

this will list all the ftp clients currently installed on your system. as well as giving you all the available clients for installation.

---

