---
title: "squeezebox server won't start"
date: 2012-01-17
forum: Multimedia Software
---

### Post by hodad on 2012-01-17
I just installed logitech media server from their website.  According to Logitech's instructions, I then went to terminal and typed:

service squeezeboxserver start

And got the result 

"service not found" (not sure if this was exact wording, but similar)

I then tried installing from Synaptic.  Synaptic found the application already installed (as Logitech Media Server), and asked if I wanted to reinstall.  I went ahead and did that succesfully.

The next step was to repeat: 

service squeezeboxserver start

to which I got the following:

squeezeboxserver: unrecognized service

Anyone know what's going on?

Thanks!

---

### Post by nothingspecial on 2012-01-17
As is often the case, things change but documentation doesn't

```
sudo service logitechmediaserver start
```

Should start automatically though.

---

### Post by hodad on 2012-01-17
I found out that the name was changed from what they listed in their online instructions.  I noticed that the downloaded files were names logitechmediaserver instead of squuezeboxserver, so I ran the following from the terminal:

service logitechmediaserver start

and it worked.

---

### Post by hodad on 2012-01-17
nothingspecial - sorry, I noticed your response after I fixed the problem.

Thanks for your response, though!  Now I can program the radio 

:D

---

### Post by nothingspecial on 2012-01-17
> **hodad said:**
> nothingspecial - sorry, i noticed your response after i fixed the problem.

Thanks for your response, though!  Now i can program the radio 

:d

:)

---

