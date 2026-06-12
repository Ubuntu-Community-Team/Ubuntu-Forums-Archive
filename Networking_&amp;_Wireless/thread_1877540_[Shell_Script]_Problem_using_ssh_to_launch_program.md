---
title: "[Shell Script] Problem using ssh to launch programs remotely"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by GuilhermeBrant on 2011-11-08
Hi,

I have a script which connects to a remote pc via ssh and then executes some commands. It used to work correctly, but now when I execute it, it gives me some strange errors.
Here's the script :

```


    ssh user@host << EOI
    echo "Starting player \n:"
    player mycfg.cfg &
    sleep 3
    cd $folder
    echo "Launching program \n"
    ./MyControlCode
    EOI

```      

Player is an application used as a layer between software and hardware for robot and sensor control. It acts as a server so I can connect a client (which in this case is the program MyControlCode) to it, both in the remote PC. The physical computer is used just to launch the script. 

But when I run the above script I get some error trying to open the server connection, or, depending on the remote PC I'm using, it gives an "error while loading shared libraries".

What I find odd about it, is that some months ago, the same script worked fine, and when I mannually ssh to user@host and execute "player", it also works.

Can someone enlighten me on this one?

Thanks in advance,
Luiz.

---

