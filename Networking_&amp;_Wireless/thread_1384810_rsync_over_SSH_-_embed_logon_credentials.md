---
title: "rsync over SSH - embed logon credentials"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by ripeart on 2010-01-18
Hi! Is there a way to embed the user password in the following code? 

```
rsync -r -n --progress --delete -u -l -e ssh 192.168.1.9:/Volumes/1TB_Internal/Music "/media/Storage/Libraries/My Music"
```The machine I'm syncing to is running OSX 10.4 if that makes a difference. I'm also wondering if there is a way to embed a particular user for the SSH session. My goal is to periodically rsync without my intervention.

---

### Post by ripeart on 2010-01-18
OK got it working. :D Please follow the directions at this link:

[http://blogs.sun.com/jkini/entry/how_to_scp_scp_and](http://blogs.sun.com/jkini/entry/how_to_scp_scp_and)
[FONT=Arial Narrow][SIZE=2]
[/SIZE][/FONT] [FONT=Arial Narrow][SIZE=2]Lets say you want to copy between two hosts [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**host_src** [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]and [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**host_dest**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]. [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**host_src **[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]is the host where you would run the [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]scp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]ssh [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]or [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]rsyn [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]command, [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**irrespective of the direction of the file copy**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]![/SIZE][/FONT]
 [FONT=Arial Narrow][SIZE=2]On [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**host_src**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], run this command as the user that runs [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]scp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]/[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]ssh[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]/[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]rsync[/SIZE][/FONT]

        ```
 $ ssh-keygen -t rsa
```         [FONT=Arial Narrow][SIZE=2]This will prompt for a passphrase. Just press the  enter key. It'll then generate an identification (private key) and a  public key. Do not ever share the private key with anyone!         ssh-keygen shows         where it saved the public key. This is by default ~/.ssh/id_rsa.pub:[/SIZE][/FONT]
         [FONT=Arial Narrow][SIZE=2]Your         public key has been saved in <your_home_dir>/.ssh/id_rsa.pub[/SIZE][/FONT]                 
  [FONT=Arial Narrow][SIZE=2]Transfer the  [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]id_rsa.pub [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]file to [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]host_dest [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]by either [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]ftp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]scp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]rsync [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]or any other method.[/SIZE][/FONT]         
        
  [FONT=Arial Narrow][SIZE=2]On **host_dest**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], login as the remote user which you plan to use when you run [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]scp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]ssh [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]or [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]rsync [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]on **host_src**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2].[/SIZE][/FONT]    
             
 [FONT=Arial Narrow][SIZE=2]Copy the contents of [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]id_rsa.pub [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]to [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]~/.ssh/authorized_keys[/SIZE][/FONT]. [FONT=Arial Narrow][SIZE=2]Note that **ssh** by default does not allow root to log in. This has to be explicitly enabled on **host_dest**.   This can be done by editing **/etc/ssh/sshd_config****PermitRootLogin**  from **no**  to **yes**.  Don't forget to restart **sshd** so that it reads the modified config file. Do this ***only*** if you want to use the root login. [/SIZE][/FONT]

  [FONT=Arial Narrow][SIZE=2]Well, thats it. Now you can run [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]scp[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2], [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]ssh [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]and [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]rsync [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]on **host_src** [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]connecting to **host_dest** [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]and it won't prompt for the password. Note that this will still prompt for the password if you are running the commands on [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]host_dest [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]connecting to **host_src**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]. You can reverse the steps above (generate the public key on **host_dest** [/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]and copy it to **host_src**[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]) and you have a two way setup ready![/SIZE][/FONT]

---

### Post by Lars Noodén on 2010-01-19
> **ripeart said:**
> This can be done by editing **/etc/ssh/sshd_config****PermitRootLogin**

You might want to really reconsider that.  Which program do you need to run as root?  Figure that out and then set up sudoers to allow it to be run by the account with the key.  It's simple regex.

---

### Post by ripeart on 2010-01-19
It's not so much that I want to run a program, its more like I need to pass network credentials for the remote computer over my LAN so that I don't have to authenticate every time.

By the way, I was never able to complete the *This can be done by editing /etc/ssh/sshd_config**PermitRootLogin *step.I couldn't find that file!

---

### Post by Lars Noodén on 2010-01-19
> **ripeart said:**
> It's not so much that I want to run a program, its more like I need to pass network credentials for the remote computer over my LAN so that I don't have to authenticate every time.

By the way, I was never able to complete the *This can be done by editing /etc/ssh/sshd_config**PermitRootLogin *step.I couldn't find that file!

**PermitRootLogin** is a configuration directive inside /etc/ssh/sshd_config.  It should be set to **no**

Ok.  Then it's inadvisable to log in remotely as root, especially without a passphrase.  

If you want to be able to log in repeatedly without having to do the password each time.  Use key-based authentication for the account you are logging in with.  Use a good pass-phrase so that it's safe.

The trick then to avoiding using the password is to use **ssh-agent** to hold the key.  Before you connect for the first time, load the key into **ssh-add**

```

ssh-add ~/.ssh/my_key_rsa

```

After that, ssh, scp and sftp will all read the key in the agent when trying to connect.

---

