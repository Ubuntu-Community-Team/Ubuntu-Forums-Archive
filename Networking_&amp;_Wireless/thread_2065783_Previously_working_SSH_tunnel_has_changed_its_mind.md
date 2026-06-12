---
title: "Previously working SSH tunnel has changed its mind"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by Mezzoforte on 2012-10-02
(Running Ubuntu 12.04, 64-bit)

I'm connecting over SSH (with key authentication) to my computer on the other side of the globe. This worked a while ago, but doesn't anymore. I'm using Ubuntu 12.04 on the remote as well as local side.

To connect, I simply run the following command but with my own details:
```
ssh [name]@[ip address] -D [port]
```

Again, it used to work. It worked both from my home network, and from abroad. The router is set up to allow connections on the particular port I use.

Now what happens is just that I get a connection time-out:
```
ssh: connect to host [ip address] port 22: Connection timed out
```

There seems to be something I don't understand here since the error says the port is 22, although I've specified another port. Perhaps I've mixed up the options. Just to make sure, I tried the following command too:
```
ssh [name]@[ip address] -p [port]
```
and then the error message changes to
```
ssh: connect to host [ip address] port [chosen port]: Connection timed out
```

I am able to ping the ip address (although the response times are about 300 milliseconds, not sure if that's normal) and I have made sure that the ip address is correct (it was checked today, and it rarely changes).

What might have gone wrong? The computer is up and running, and nobody has been able to change any settings on it. This is a bit of a tricky issue since I don't have physical access to the computer. Somebody else has though, but that person is not very technically able :)

---

### Post by erikringmar on 2012-10-14
I'm having a related problem. While the SSH tunnel is connecting nicely via the terminal, the proxy settings in 12.04 are all screwy. Can't seem to make Chrome etc recognize the tunnel I've opened up.

Any ideas?

Erik

---

