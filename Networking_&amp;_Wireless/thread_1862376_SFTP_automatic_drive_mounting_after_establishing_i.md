---
title: "SFTP automatic drive mounting after establishing internet connection problem"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by Lowermind on 2011-10-16
Hello,

Ive written a very basic script in bash and placed it in
/etc/NetworkManager/dispatcher.d/
(scripts from there are being run after establishing connection)

The following code does everything properly when I manually run it but outputs only errors when it is run automatically by NetworkManager. 

Additionally after startup of the system and connecting to the network system launches two instances of the program. 

What could fix the problem?

```

#!/bin/bash

output=""

while [ -z "$output" ]; do
output=$(echo "password" | sshfs username@ip: /home/piotr/DRIVES -o password_stdin 2>&1)
if [ -z "$output" ]; then
break
else
echo "$output" | cat >> /home/piotr/mounting_errors.txt 
output=$(echo "$output" | grep "fuse" >&1)
sleep 1
fi
done

```

it outputs errors to mounting_errors.txt :
first few

"read: Connection reset by peer"

then a lot of

"Timeout waiting for prompt"


Im running Ubuntu 11.10.

---

