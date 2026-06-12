---
title: "Best Android app for ssh communication with LAN"
date: 2017-12-10
forum: Mobile Technology Discussions (CLOSED)
---

### Post by makem2 on 2017-12-10
I am using ssh keys but am new to this. I tried an app called Juice but it did not find the public key on my Galaxy s8

I'm looking for a good reasonably priced app which can use the same key type which I made in xubuntu.

---

### Post by TheFu on 2017-12-12
Public ssh keys don't belong on the client.  public keys are placed on the remote sshd server to be used for validation by the local ssh client with the private ssh-key.  [https://sonelli.freshdesk.com/support/solutions/articles/139632-juicessh-supported-private-key-formats-openssh-pem-](https://sonelli.freshdesk.com/support/solutions/articles/139632-juicessh-supported-private-key-formats-openssh-pem-)  Only specific ssh-key formats can be used.

Juice is one of 2 ssh clients available that are worth your time based on conversations I've had with others. **Termux** is the other.

I would look in the f-droid app-store for alternatives.  No need to pay for an ssh-client.

---

### Post by makem2 on 2017-12-12
> **TheFu said:**
> Public ssh keys don't belong on the client.  public keys are placed on the remote sshd server to be used for validation by the local ssh client with the private ssh-key.  [https://sonelli.freshdesk.com/support/solutions/articles/139632-juicessh-supported-private-key-formats-openssh-pem-](https://sonelli.freshdesk.com/support/solutions/articles/139632-juicessh-supported-private-key-formats-openssh-pem-)  Only specific ssh-key formats can be used.

Juice is one of 2 ssh clients available that are worth your time based on conversations I've had with others. **Termux** is the other.

I would look in the f-droid app-store for alternatives.  No need to pay for an ssh-client.

Thank you, I had never heard of F-Droid

---

### Post by brandoncruz29 on 2018-01-26
F-Droid is great. I always check it out first. You can usually find what you need there.

---

