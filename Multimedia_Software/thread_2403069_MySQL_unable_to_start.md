---
title: "MySQL unable to start"
date: 2018-10-07
forum: Multimedia Software
---

### Post by TUOggy on 2018-10-07
I recently purchased a Rock64 board (4gb of memory) to set up as a media and basic web development server (this is not a production environment).
I downloaded Ubuntu from [https://github.com/ayufan-rock64/linux-build/releases](https://github.com/ayufan-rock64/linux-build/releases) (I know it's not an official version, but I couldn't get the official to work with this board)

I set it up as a lamp server and got everything working with default settings. 

I'm using a 32GB eMMC drive for the OS, and a 1.5TB hdd (mounted at /mnt/media/) as my web drive. 

So, I changed my server root directory in Apache to /mnt/media/www/ (everything is still working)

I then wanted to change my MySQL directory to /mnt/media/mysql/ following these directions:
[https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-18-04)

Before I could do that, I had to change the password though, but I realized that MySQL was now using a different auth method than I'm used to, so I followed these steps to go back to using a root password instead of auth_socket:

```
$ sudo mysql -u root # I had to use "sudo" since is new installation

mysql> USE mysql;
mysql> UPDATE user SET plugin='mysql_native_password' WHERE User='root';
mysql> FLUSH PRIVILEGES;
mysql> exit;

$ service mysql restart
```

Everything was still working, and I was able to log in using a root password now.

I walked through everything to complete the directory change per the above directions (minus the apparmor bit, because it's not included), and rebooted MySQL (or tried to) and it failed. 

When I did a service mysql status, I got the following:

```
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Sun 2018-10-07 10:46:45 UTC; 12s ago
  Process: 1215 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid (code=exited,
  Process: 1206 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)

Oct 07 10:46:45 rock64 systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Oct 07 10:46:45 rock64 systemd[1]: mysql.service: Scheduled restart job, restart counter is at 5.
Oct 07 10:46:45 rock64 systemd[1]: Stopped MySQL Community Server.
Oct 07 10:46:45 rock64 systemd[1]: mysql.service: Start request repeated too quickly.
Oct 07 10:46:45 rock64 systemd[1]: mysql.service: Failed with result 'exit-code'.
Oct 07 10:46:45 rock64 systemd[1]: Failed to start MySQL Community Server.
```

I tried checking Google, and everywhere else, but I'm at a loss.
Any advice would be greatly appreciated.

---

### Post by TUOggy on 2018-10-09
Still trying to figure this one out.
Is there anything else that I can search for to help with this?

---

