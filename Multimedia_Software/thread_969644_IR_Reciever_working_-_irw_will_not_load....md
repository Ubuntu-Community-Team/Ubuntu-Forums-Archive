---
title: "IR Reciever working - irw will not load..."
date: 2008-11-03
forum: Multimedia Software
---

### Post by hinge on 2008-11-03
I have an IR receiver from irblaster.
I have loaded the lirc_serial using the User-space I2C driver.

I use the setserial commands as described elsewhere.

When I run 
```
sudo mode2 -d /dev/lirc0
```

I get a nice response from my remote - so I guess that it is working.

Bu I can not get irw to work. Sometimes I get a 

```
connect: Connection refused
```

other times I just get nothing.

I don't know enough about this stuff - What needs to be in place to to get this stuff running ???

is it ok to use the User-space I2C driver ?? 
I'm using a imon remote - other remotes work also

Thank you

---

