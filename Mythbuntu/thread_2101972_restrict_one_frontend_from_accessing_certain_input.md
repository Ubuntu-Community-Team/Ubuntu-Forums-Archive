---
title: "restrict one frontend from accessing certain inputs"
date: 2013-01-05
forum: Mythbuntu
---

### Post by davidstoll on 2013-01-05
I have a backend with several different inputs, but I would like one of my front ends to only access one particular input.  Is this possible?  Like for instance, I have an HDHomeRun.  Can I restict access to only the HDHomeRun and not allow the front end to access my other tuners?

Thanks

---

### Post by nickrout on 2013-01-05
> **davidstoll said:**
> I have a backend with several different inputs, but I would like one of my front ends to only access one particular input.  Is this possible?  Like for instance, I have an HDHomeRun.  Can I restict access to only the HDHomeRun and not allow the front end to access my other tuners?

Thanks
I don't think so, but tell us why you would want to as there may be other workarounds - like setting LiveTV priorities or something.

---

### Post by davidstoll on 2013-01-05
> **nickrout said:**
> I don't think so, but tell us why you would want to as there may be other workarounds - like setting LiveTV priorities or something.

I have priorities set such that my HDHomeRun will record 2 shows at the same time, but if you then try to watch live tv, it kicks over to another input/source.  Which makes complete sense, but I only want it to use the one input and act as if there are no available inputs in that particular situation.

---

### Post by nickrout on 2013-01-06
In backend setup set the homerun to have the lowest priority on livetv and highest for recording.

---

### Post by davidstoll on 2013-01-06
> **nickrout said:**
> In backend setup set the homerun to have the lowest priority on livetv and highest for recording.

That will definitely give me the best possible case for prioritizing inputs, but will not restrict a particular front end from accessing a particular input.

---

### Post by nickrout on 2013-01-06
No but the frontend will be less likely to acces sit if it goes through the other options first.

Also you are aware your HDHR can operate as multiple virtual tuners? Utilising this may alleviate your problem.

---

### Post by davidstoll on 2013-01-06
> **nickrout said:**
> No but the frontend will be less likely to acces sit if it goes through the other options first.

Also you are aware your HDHR can operate as multiple virtual tuners? Utilising this may alleviate your problem.

I'm not sure how to make it use the multiple tuners.  I just thought it used it automatically.  But still, the other channels are available.

---

