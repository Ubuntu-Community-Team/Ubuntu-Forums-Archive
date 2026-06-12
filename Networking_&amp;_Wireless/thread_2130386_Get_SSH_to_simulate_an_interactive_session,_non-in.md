---
title: "Get SSH to simulate an interactive session, non-interactively"
date: 2013-03-29
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2013-03-29
I'm trying to connect to a shell server via ssh non-interactively, however it seems to treat sessions quite differently based on whether or not it is an interactive or non-interactive session.  Basically, I want to be able to send this command:
```
ssh me@shell.example.com "cd directory; ./script.sh"
```
AS IF I had, as separate commands, ran:
```
me@computer:~$ ssh me@shell.example.com
[me@shell ~]$ cd directory
[me@shell ~/directory]$ ./script.sh
```


How do I do this so the shell server thinks I am running an interactive session even if I'm not?

---

### Post by SeijiSensei on 2013-03-29
There's nothing wrong with the command you gave, though I would use a full path to cd, e.g., "cd /path/to/some/directory".  Alternatively you can just put the script in a location in your PATH, or invoke the script with a full path like "/path/to/some/directory/script.sh".  It depends on whether the script expects to find other files it needs to work with in the same directory as itself.  If the script uses full paths, then the "cd directory" command is probably unnecessary.

If you want to send commands via SSH, you should set up [public-key authentication]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to avoid being prompted for a password.

---

### Post by Stonecold1995 on 2013-03-29
> **SeijiSensei said:**
> There's nothing wrong with the command you gave, though I would use a full path to cd, e.g., "cd /path/to/some/directory".  Alternatively you can just put the script in a location in your PATH, or invoke the script with a full path like "/path/to/some/directory/script.sh".  It depends on whether the script expects to find other files it needs to work with in the same directory as itself.  If the script uses full paths, then the "cd directory" command is probably unnecessary.

If you want to send commands via SSH, you should set up [public-key authentication]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") to avoid being prompted for a password.
I don't think you understand my question.  I'm not asking how to run a script non-interactively.  I can already do that and it works.

Yes the script uses relative paths, so I have to use cd before running it.  And I already have public-key authentication set up.

The issue though, is that the server will "treat" me differently if I'm in an interactive session vs non-interactive.  I want to "trick" the server into thinking it's interactive.

Specifically, the shell account will disconnect me after one hour in an interactive session to prevent using too much bandwidth (i.e. someone forgets they're connected and stay on for too long).  However if it's non-interactive the server disconnects after about 40 seconds, probably to prevent abuse.  I need a little over 40 seconds of non-interactive connection, so I need a way to tell the server it is interactive when it's not.

Would "expect" help me with this?  If so how could I use it for this purpose?

---

### Post by SeijiSensei on 2013-03-29
I leave SSH sessions open in a terminal for days without disconnecting.  Do you have control over both ends of the connection?  It doesn't sound like it.

I don't know about expect.  Forty seconds is a long time for running a script.  (Mine usually complete in a couple of seconds or less.)  What is it waiting for?

What if the script spawns a job in the background that pings your end of the session once per second (the default) and ends after a minute like this:

```
ping -c 60 ip.address.of.client > /dev/null &
```

---

### Post by Stonecold1995 on 2013-03-29
I do not have control over both ends.  It is a free shell account.

The script scrapes a few URLs, saves it to a file, and exits.  But the server uses Tor, so it is much slower than normal, making it take slightly too long.

What would pinging my client do?

I cannot run any processes unless I'm connected.  The main limitations per account are 1) no processes can run in the background while you're away, 2) only two simultaneous connections can be established, and 3) only 16 processes (including bash, sshd, etc) can be run at once.

---

### Post by mharv on 2013-03-30
You must use Expect or Expect-lite:
[http://www.nist.gov/el/msid/expect.cfm](http://www.nist.gov/el/msid/expect.cfm)
[http://expect-lite.sourceforge.net/](http://expect-lite.sourceforge.net/)

---

### Post by Stonecold1995 on 2013-03-30
> **mharv said:**
> You must use Expect or Expect-lite:
[http://www.nist.gov/el/msid/expect.cfm](http://www.nist.gov/el/msid/expect.cfm)
[http://expect-lite.sourceforge.net/](http://expect-lite.sourceforge.net/)
How can I use expect to do this?  The syntax is very confusing...

It has to do this:
1) ssh into a server
2) cd into a directory
3) run a script (the script closes the ssh connection automatically when it's finished)
4) wait a certain amount of time
5) goto step 1

Currently I have:
```
expect << EOD
spawn ssh me@shell.example.com
expect 'me@shell'
send "cd directory; ./script.sh\n"
expect 'me@shell'
send "logout\n"
EOD
```

However it seems to be randomly exiting in the middle, as in expect itself closes, which kills its child (ssh).  How can I get it to actually wait before dying on me?

---

### Post by Lars Noodén on 2013-03-30
You might be able to keep the connection open by using the options [ServerAliveInterval and ServerAliveCountMax](http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html) on your client.  They can be specified in the shell as runtime arguments or added to ~/.ssh/config once you find settings that you want to keep and make permanent.

---

### Post by Stonecold1995 on 2013-03-30
> **Lars Noodén said:**
> You might be able to keep the connection open by using the options [ServerAliveInterval and ServerAliveCountMax]("http://manpages.ubuntu.com/manpages/precise/en/man5/ssh_config.5.html") on your client.  They can be specified in the shell as runtime arguments or added to ~/.ssh/config once you find settings that you want to keep and make permanent.
Uh, it has nothing to do with ssh closing the connection...   ssh dies because expect closes, and expect is ssh's parent, so naturally ssh is killed.

I want expect to wait until the script has finished running (and the normal prompt is again displayed), at which point it should send "logout\n".  *How can I get it to do that?*

---

### Post by The Cog on 2013-03-30
I know that running a command under ssh gets treated differently to running it in an ssh shell login. For example, top works in a normal ssh shell login, but fails when run as "ssh hostname top" with error "TERM environment variable not set.".

But for what you are trying to do, can I suggest using screen? Screen acts as a screen-buffer between you and the commands you run. You can set a program running in screen, disconnect, reconnect later and see the program still running. You can even run several programs, hot-key between the virtual screens. I use it (for instance) I do an upgrade that must not be interrupted but I'm doing it by ssh over a flakey network. If the network fails and disconnects me, I just reconnect and see where the update has got to.

---

### Post by Stonecold1995 on 2013-03-30
> **The Cog said:**
> But for what you are trying to do, can I suggest using screen? Screen acts as a screen-buffer between you and the commands you run. You can set a program running in screen, disconnect, reconnect later and see the program still running. You can even run several programs, hot-key between the virtual screens. I use it (for instance) I do an upgrade that must not be interrupted but I'm doing it by ssh over a flakey network. If the network fails and disconnects me, I just reconnect and see where the update has got to.
Using screen isn't allowed to prevent abuse of the free account.

---

### Post by Stonecold1995 on 2013-03-30
Ok, so this is *exactly* what I'm running, word for word:
```
alex@kubuntu:/tmp$ cat test.sh
#!/bin/bash

while true; do
    expect << EOD
spawn ssh stonecold@shell.cjb.net
expect 'stonecold@shell'
send "cd gelbooru; ./scrape_deleted.sh\n"
expect 'stonecold@shell'
send "logout\n"
EOD
echo "Done, sleeping 1 hour"
sleep 1h
echo "Restarting"
done
alex@kubuntu:/tmp$ ./test.sh
spawn ssh stonecold@shell.cjb.net
Last login: Sat Mar 30 05:58:58 2013 from 46.165.196.138
[stonecold@shell ~]$ cd gelbooru; ./scrape_deleted.sh
Started Sat Mar 30 05:59:29 MDT 2013
Scraping post 51303
Scraping post 51304
Scraping post 51305
Scraping post 51306
Scraping post 51307
Scraping post 51308
Scraping post 51309
Scraping post 51310
Scraping post 51311
Scraping post 51312
Scraping post 51313
Scraping post 51314
Scraping post 51315
Scraping post 51316
Scraping post 51317
Scraping post 51318
Scraping post 51319
Done, sleeping 1 hour
^C
```

I had to control+c because it only exits and says "Done, sleeping for 1 hour" when ssh (and expect) closes.

So the shell server is disconnecting very soon after I connect, and I need the script to be able to run a little while longer.

**When I connect normally, run "cd gelbooru" and "./scrape_deleted.sh", I remain connected for a full hour if I have to.  When I connect either using expect or " ssh stonecold@shell.cjb.net 'cd gelbooru; ./scrape_deleted.sh' ", it disconnects in several seconds.  HOW to I prevent this specifically?**

---

### Post by mharv on 2013-03-30
Those links should answer your question, but I've never needed to do that so I've not tested it out.
[http://lists.samba.org/archive/linux/2011-April/029884.html](http://lists.samba.org/archive/linux/2011-April/029884.html)
[http://www.linuxquestions.org/questions/programming-9/can-expect-return-control-of-a-spawned-process-to-a-shell-script-770340/](http://www.linuxquestions.org/questions/programming-9/can-expect-return-control-of-a-spawned-process-to-a-shell-script-770340/)

---

### Post by Stonecold1995 on 2013-03-30
> **mharv said:**
> Those links should answer your question, but I've never needed to do that so I've not tested it out.
[http://lists.samba.org/archive/linux/2011-April/029884.html](http://lists.samba.org/archive/linux/2011-April/029884.html)
[http://www.linuxquestions.org/questions/programming-9/can-expect-return-control-of-a-spawned-process-to-a-shell-script-770340/](http://www.linuxquestions.org/questions/programming-9/can-expect-return-control-of-a-spawned-process-to-a-shell-script-770340/)
Those don't really tell me anything...

Is it "expect eof"?  I have no idea what that does.

---

### Post by Stonecold1995 on 2013-03-30
I think I've found a way to get it to work, sort of.

I just created .bash_profile with contents that would run the script automatically.  Then all I have to do is ssh into it to run the script, without needing expect.

Let's see how this goes.

---

### Post by mharv on 2013-03-31
Best of luck, hope it works.

---

### Post by Lars Noodén on 2013-03-31
> **Stonecold1995 said:**
> I just created .bash_profile with contents that would run the script automatically.  Then all I have to do is ssh into it to run the script, without needing expect.

Since you already have public key authentication set up it might work to put **command="*somecommand*"** in your  ~/.ssh/authorized_keys.  The details are in the man page for [sshd](http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html) in the section "AUTHORIZED_KEYS FILE FORMAT"  That will allow you to run your script yet still have shell access when you need it.

---

### Post by Stonecold1995 on 2013-03-31
> **Lars Noodén said:**
> Since you already have public key authentication set up it might work to put **command="*somecommand*"** in your  ~/.ssh/authorized_keys.  The details are in the man page for [sshd]("http://manpages.ubuntu.com/manpages/precise/en/man8/sshd.8.html") in the section "AUTHORIZED_KEYS FILE FORMAT"  That will allow you to run your script yet still have shell access when you need it.
I just have this in my .bash_profile:
```
#!/bin/bash

echo "Starting scraper in 10 seconds.  Press ctrl+c to cancel."
if sleep 10; then
    cd gelbooru
    ./scrape_deleted.sh
    cd "$OLDPWD"
fi
echo
```

So I'll still be able to work if I want to, otherwise if it's pseudo-interactive it'll just go on and run the script.

Looks like problem solved!

---

