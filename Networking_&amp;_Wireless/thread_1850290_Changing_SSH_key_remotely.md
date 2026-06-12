---
title: "Changing SSH key remotely"
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by freshtoast on 2011-09-26
Hello,

Currently, whenever I change the client key for my SSH connection I do it physically on the server i.e. copy the key from the client onto a memory stick then plug that into the server and update authorized_keys.

I want to be able to do this remotely from the client, over the SSH connection without locking myself out!

Is the best way to do this to use SCP to append the new key to the authorized_keys, then delete the old key in authorized_keys? If so, any suggestions on an easy syntax to accomplish that?

Many thanks

---

### Post by nothingspecial on 2011-09-26
```
ssh-copy-id user@ip_of_host
```

Lots of other ways here

[http://askubuntu.com/questions/4830/easiest-way-to-copy-ssh-keys-to-another-machine#4833](http://askubuntu.com/questions/4830/easiest-way-to-copy-ssh-keys-to-another-machine#4833)

---

### Post by freshtoast on 2011-09-26
Thank you for your reply.

I may not have fully understood the ssh-copy-id, but surely this creates a chicken/egg scenario? I can only log in to the ssh with a key (no password logins), so I can't connect to the ssh server to copy the identity's key until the key is already in the authorized_keys list.

Would I have to use keygen to create another key with a different name and then specify that for the ssh-copy-id? Would it append or replace authorized_keys?

Apologies for yet more questions!

---

### Post by Kelketek on 2011-09-26
Seeing as how you have physical access to the server anyway, there's little harm in experimenting.

You shouldn't get kicked out if you change the keys live. After all, you may be editing the file, but it's not like SSH is going to read that file again until another connection is established. You're already in, so it's not going to check the keyfiles until you try to authenticate once more. Heck, you can even restart the SSH daemon through SSH (and even the network service) in most instances and still be connected because it's smart enough to let the connection persist. Go ahead and try this to confirm that it works in your scenario, but it should.

---

