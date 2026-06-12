---
title: "Hamachi up and down with network"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Beacon11 on 2009-05-05
Hello all. I didn't see this anywhere else, so I wanted to share.

     There are plenty of tutorials out there both for installing hamachi and writing init scripts for hamachi. I had this all set up, but still found it unsatisfactory as hamachi was started whether the computer was connected to a network or not. Therefore, I decided it was time to write a script that did the following:

[LIST]
[*]When NetworkManager connects to a network
[LIST]
[*]Run tuncfg
[*]Start hamachi
[*]Make sure hamachi is logged in
[*]Grab hamachi client nicknames
[/LIST]
[*]When NetworkManager disconnects from a network
[LIST]
[*]Stop hamachi
[*]Kill tuncfg
[/LIST]
[/LIST]

     This tutorial will assume you know a bit about Linux, but if you follow all the commands exactly, I'm willing to bet you'll get it working even if you feel you have inadequate experience.

     Please note that I am using 32-bit Ubuntu 9.04, and the default NetworkManager versus alternatives.

     To do this, you need to create a new NetworkManager dispatch script.

```

cd /etc/NetworkManager/dispatcher.d/

```

     There should be at least one file in this directory already. The file names here are prepended with numbers indicating the script priority. For example, 01ifupdown will run first, 02scriptname will run second, etc. Since hamachi can probably run last, check to see what priority numbers are already assigned:

```

ls

```

     In my case, I only had one file in this directory, 01ifupdown. Therefore, I called my new hamachi script 02hamachiupdown.

```

# Create a new file with your favorite editor (sudo for owner and group info)
sudo vi 02hamachiupdown

```

     The contents of this script should be the following:

```

#!/bin/sh -e
# Script to start and stop hamachi depending on the current
# state of NetworkManager

# This is the system username for the hamachi account you wish to
# activate. Of course, this assumes you installed the hamachi
# configuration in the user's home directory (default hamachi
# installation) rather than some alternate path.
USER=InsertYourUserNameHere

case "$2" in
        up) # We've connected to a network
                /sbin/tuncfg
                /bin/su - $USER -c "hamachi start"
                /bin/su - $USER -c "hamachi login"
                /bin/su - $USER -c "hamachi get-nicks"
                ;;
        down) # We've disconnected from a network
                /bin/su - $USER -c "hamachi stop"
                /usr/bin/killall tuncfg
                ;;
esac

```

     Replace InsertYourUserNameHere with your username. If you're unsure of what this is, it's what's printed if you run

```

whoami

```

Almost done! Another thing you need to do is make the script properly executable:

```

sudo chmod 755 02hamachiupdown

```

     Please note that this script is best for single-user systems, as it statically runs hamachi. What I mean by this is that only a single, hard-coded hamachi account will be run. With the way the script is currently written, the hamachi configuration files must be in the user's home directory. If you have multiple users, this script will only run one user's hamachi, not necessarily the user currently logged in. Also, if you have the hamachi configuration files stored in an alternate, more global location (say... /etc/hamachi) this script will need to be altered (which I can certainly do if anybody needs this).

     While this script does function as required, I am by no means an expert shellcoder, and the script can most likely be improved. If that is indeed the case, please let me know and I can update the script.

---

