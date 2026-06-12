---
title: "HOWTO set up Juniper Network Connect VPN on Ubuntu 9.10"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by edsap on 2009-11-19
I could not connect to my company's private VPN via Juniper Network Connect after I installed Ubuntu 9.10 on my laptop. It took me a lot of time to search the web for the answer. After doing some trials and errors, I found the solution, which turned out quite simple. Hopefully, this solution will work for you too.  Here you go:

_**PROBLEM**_: After I click on the [start] button of the Network Connect prompt on the Juniper Network VPN screen, I got the error message saying something like "JRE is disabled or not installed" and I got stuck there.

_**SOLUTION: **_

[LIST=1]
[*]   Install Sun Java runtime
[*]   Create a root password and give it to the Juniper setup program when it asks for it. You only need to do this on the first connect. Then ignore such request thereafter.
[*]   Restart the browser and start the Network Connect again. It should work.
[/LIST]

* Here are the detail steps for the solution. First, I opened the Terninal since all the work will be done at the command line.

1. To install the Sun Java runtime, issue the following command:

   **[FONT=Courier New] sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts[/FONT]**

- Then run Java to make sure that it works.

[FONT=Courier New]**    java -version**
         (the output looks like the followings):
         java version "1.6.0_15"
         Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
         Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)[/FONT]

- Run Firefox and make sure that it has Java plugins by issuing the "about:plugins" command at the URL box and look for java plugins:

     **about:plugins**

2. Create a root password, by issuing the following command. You will be asked for your sudo password and then the new root password, as follows:

    **[FONT=Courier New] sudo passwd root[/FONT]**
        [sudo] password for <your-user-name-here>: 
        Enter new UNIX password: ***<root-password>***
        Retype new UNIX password:*** <root-password>***
        passwd: password updated successfully

3. Now run Firefox and open your Juniper Private Network page, locate the Network Connect section and click the [start] button. Then the followings happen:

- The Java console opens.
- The installINC.sh window opens. When this window then asks for the root/su password, give it the root password that you created earlier. It asks something like this:

   ** Please enter root/su password: *[FONT=Courier New]<root-password>[/FONT]***
[B]
- Now, close the Java console. You do not need it anymore.[/B]
[B]- Also, close the installINC.sh window, if it does not close by itself.
[/B]
Now, the Network Connect windows opens. You can minimize it. But do not close it. You need to keep it open so that you can access your private network.

4. Now you can ssh to your private network and starting working.

  **[FONT=Courier New] ssh <your-private-domain>[/FONT]**

5. After you are tired of working, log out of your private network and click on the [SignOut] button on the Network Connect window to close it.

That's it! :popcorn:

---

### Post by sotomajor on 2009-11-23
Everything worked fine few days ago, but today I've got troubles: it asks password, then closes prompt window and do nothing.

Found some error message in the log:

[B]mkotsur@n-fox:~/.juniper_networks/network_connect$ cat ncui.log 
20091123220532.217961 ncui[p2274.t2298] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20091123220532.218032 ncui[p2274.t2298] ncui.info read from params...  (nccommon.cpp:121)
20091123220532.218175 ncui[p2274.t2298] ncapp.panic Failed to read password from prompt (nccommon.cpp:614)
[/B]
Yes, I have root user and it's password is correct.

---

### Post by GsL9vBab on 2009-11-30
Thanks for posting this.  I seem to be missing a piece to this puzzle.  You mention installNC.  Is this part of the Juniper software release?  Are you connecting to the firewall's webface on your company's public IP?

Many thanks for any further insight you can offer.

Peter

[QUOTE=edsap;8351211]I could not connect to my company's private VPN via Juniper Network Connect after I installed Ubuntu 9.10 on my laptop. It took me a lot of time to search the web for the answer. After doing some trials and errors, I found the solution, which turned out quite simple. Hopefully, this solution will work for you too.  Here you go:

---

### Post by sotomajor on 2009-11-30
> **GsL9vBab said:**
> ...Hopefully, this solution will work for you too.  Here you go:
And what's solution?

---

### Post by akshay.ranjan on 2009-12-22
I was able to connect to Juniper network connect on my Jaunty laptop some days back. Now I can't; whenever I try to connect to VPN, the JAVA window appears, IP address is assigned but the connection goes to SSL/deflate after some time. I know that ESP mode is required for my VPN to work. Help??

sudo ldd ncsvc
    linux-gate.so.1 =>  (0xb7f13000)
    libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7efd000)
    libz.so.1 => /lib/libz.so.1 (0xb7ee7000)
    libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7ecd000)
    libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ea7000)
    libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d44000)
    /lib/ld-linux.so.2 (0xb7f14000)

./ncsvc --v
Juniper Network Connect Server for Linux.
Version         : 6.4
Release Version : 6.4-0-Build14063
Build Date/time : Mar 11 2009 09:29:32 
Copyright 2001-2008 Juniper Networks

ls -alt | grep libssl
lrwxrwxrwx   1 root root       24 2009-12-20 04:40 libssl.so.2 -> /usr/lib/libssl.so.0.9.8
lrwxrwxrwx   1 root root       10 2009-11-27 04:43 libssl3.so.1d -> libssl3.so
lrwxrwxrwx   1 root root       20 2009-11-27 04:41 libssl.so.0.9.8 -> /lib/libssl.so.0.9.8
-rw-r--r--   1 root root   191432 2009-08-25 09:27 libssl3.so

 ls -alt | grep libstdc++
lrwxrwxrwx   1 root root       31 2009-12-20 04:39 libstdc++-libc6.2-2.so.3 -> libstdc++-3-libc6.2-2-2.10.0.so
lrwxrwxrwx   1 root root       19 2009-11-27 04:30 libstdc++.so.6 -> libstdc++.so.6.0.10
-rw-r--r--   1 root root   950424 2009-03-17 09:28 libstdc++.so.6.0.10
-rw-r--r--   1 root root  1292301 2005-11-20 04:25 libstdc++-3-libc6.2-2-2.10.0.so

---

### Post by sotomajor on 2009-12-22
> **sotomajor said:**
> Everything worked fine few days ago, but today I've got troubles: it asks password, then closes prompt window and do nothing.

Found some error message in the log:

[B]mkotsur@n-fox:~/.juniper_networks/network_connect$ cat ncui.log 
20091123220532.217961 ncui[p2274.t2298] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20091123220532.218032 ncui[p2274.t2298] ncui.info read from params...  (nccommon.cpp:121)
20091123220532.218175 ncui[p2274.t2298] ncapp.panic Failed to read password from prompt (nccommon.cpp:614)
[/B]
Yes, I have root user and it's password is correct.

:guitar: [SIZE=5]Problem is solved for me...

[SIZE=1]After some investigations I found that problem encapsulated in the user's firefox profile. So replacing it with the clean one fixed applet starting for me.

[/SIZE][/SIZE]```

# Shutdown firefox instances
$ mv ~/.mozilla/firefox/13gda9ez.default ~/.mozilla/firefox/old_profile
$ cp -r /etc/firefox-3.5/profile ~/.mozilla/firefox/13gda9ez.default
# Start firefox

```
[SIZE=5][SIZE=1]

[/SIZE][/SIZE]

---

### Post by WockaNation on 2010-01-22
I'm currently trying to get Juniper to work on my 9.10 machine as well.  before finding this post I had already made all of the changes mentioned including setting the root password, but when I enter it in the window that pops up, that window closes and nothing else happens, not connected to network, just stuck.  I would supply logs, but I am new to linux and don't really know where to get them, any help would be appreciated.

---

### Post by sotomajor on 2010-01-22
> **WockaNation said:**
> I'm currently trying to get Juniper to work on my 9.10 machine as well.  before finding this post I had already made all of the changes mentioned including setting the root password, but when I enter it in the window that pops up, that window closes and nothing else happens, not connected to network, just stuck.  I would supply logs, but I am new to linux and don't really know where to get them, any help would be appreciated.

Please, see my previous post. **Clearing firefox profile** helped me. One of installed extensions seems to be buggy and causes the problem, but I still can't find time to make further investigations.

---

### Post by WockaNation on 2010-02-04
I reloaded my firefox profile, but it didn't fix the problem for me.  I'm still trying to get this working, so any help would be appreciated.

---

### Post by pistoheads on 2010-04-03
[QUOTE=edsap;8351211]I could not connect to my company's private VPN via Juniper Network Connect after I installed Ubuntu 9.10 on my laptop. It took me a lot of time to search the web for the answer. After doing some trials and errors, I found the solution, which turned out quite simple. Hopefully, this solution will work for you too.  Here you go:

_**PROBLEM**_: After I click on the [start] button of the Network Connect prompt on the Juniper Network VPN screen, I got the error message saying something like "JRE is disabled or not installed" and I got stuck there.

_**SOLUTION: **_

[LIST=1]
[*]   Install Sun Java runtime
[*]   Create a root password and give it to the Juniper setup program when it asks for it. You only need to do this on the first connect. Then ignore such request thereafter.
[*]   Restart the browser and start the Network Connect again. It should work.
[/LIST]

* Here are the detail steps for the solution. First, I opened the Terninal since all the work will be done at the command line.

1. To install the Sun Java runtime, issue the following command:

   **[FONT=Courier New] sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts[/FONT]**

- Then run Java to make sure that it works.

[FONT=Courier New]**    java -version**
         (the output looks like the followings):
         java version "1.6.0_15"
         Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
         Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)[/FONT]

- Run Firefox and make sure that it has Java plugins by issuing the "about:plugins" command at the URL box and look for java plugins:

     **about:plugins**

2. Create a root password, by issuing the following command. You will be asked for your sudo password and then the new root password, as follows:

    **[FONT=Courier New] sudo passwd root[/FONT]**
        [sudo] password for <your-user-name-here>: 
        Enter new UNIX password: ***<root-password>***
        Retype new UNIX password:*** <root-password>***
        passwd: password updated successfully

3. Now run Firefox and open your Juniper Private Network page, locate the Network Connect section and click the [start] button. Then the followings happen:

- The Java console opens.
- The installINC.sh window opens. When this window then asks for the root/su password, give it the root password that you created earlier. It asks something like this:

   ** Please enter root/su password: *[FONT=Courier New]<root-password>[/FONT]***
[B]
- Now, close the Java console. You do not need it anymore.[/B]
[B]- Also, close the installINC.sh window, if it does not close by itself.
[/B]
Now, the Network Connect windows opens. You can minimize it. But do not close it. You need to keep it open so that you can access your private network.


I have done the first 3 steps described above. I did it in a slightly different order. I started off resetting the root pwd and installing the Network Connect thingy. I then followed step 1 of this post...

The problem I have is the following:

After accessing the login page via Firefox and filling out username and pwd, I get to see the 'Launching Network Connect'page for a few seconds. It then tries do direct me to the start page, but no Network Connect window opens. The start page is not fully loaded and I get 2 promts saying 'no jQuery'.

Has anyone an idea what the problem is, and how I can resolve it?
Any help is greatly appreciated!

---

### Post by mayaknife on 2010-05-01
> **sotomajor said:**
> [SIZE=5]
[/SIZE]Found some error message in the log:

[B]mkotsur@n-fox:~/.juniper_networks/network_connect$ cat ncui.log 
20091123220532.217961 ncui[p2274.t2298] ncapp.info New ncapp log level set to 3 (nccommon.cpp:75)
20091123220532.218032 ncui[p2274.t2298] ncui.info read from params...  (nccommon.cpp:121)
20091123220532.218175 ncui[p2274.t2298] ncapp.panic Failed to read password from prompt (nccommon.cpp:614)[/B]
[SIZE=5][SIZE=1]
...

After some investigations I found that problem encapsulated in the user's firefox profile. So replacing it with the clean one fixed applet starting for me.
[/SIZE][/SIZE]

Thanks, that helped me as well.

I did a bit of experimenting and it turned out that I didn't need to get rid of my entire profile, I merely had to get rid of all cookies from the VPN server and associated domains.

---

### Post by XProgrammer on 2010-05-16
@ sotomajor. 


Thanks. It solved my problem too.

---

### Post by red_lego_man on 2010-08-20
Just to add my 2p worth, I did the above, but I also had to delete the .juniper_networks directory from my home directory.  Now it works. Cheers!

---

