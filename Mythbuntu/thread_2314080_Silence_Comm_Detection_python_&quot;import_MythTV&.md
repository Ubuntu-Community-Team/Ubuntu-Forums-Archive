---
title: "Silence Comm Detection python &quot;import MythTV&quot; source"
date: 2016-02-18
forum: Mythbuntu
---

### Post by gga96 on 2016-02-18
I am interested in [https://gist.github.com/tdack/7984364](https://gist.github.com/tdack/7984364) because it uses silence for comm flagging.

Part of the code called "silence.py", on line 12 it uses "import MythTV" to interface with the myth backend.   
I have tried to find the source code that the python code refers to, by searching the myth source and google,  but no joy.

I would like to write some python code using the same "import MythTV" library.

Can you help me to find the lib code please.

Cheers
Glen

---

### Post by blm-ubunet on 2016-02-18
IIUC..
The code [https://github.com/MythTV/mythtv/tree/master/mythtv/bindings/python/MythTV](https://github.com/MythTV/mythtv/tree/master/mythtv/bindings/python/MythTV) (excluding ttvdb & wikiscripts) is compiled to MythTV.py python lib bindings.

This python script appears to be involved
[https://github.com/MythTV/mythtv/blob/master/mythtv/bindings/python/setup.py](https://github.com/MythTV/mythtv/blob/master/mythtv/bindings/python/setup.py)

Rain in the last few days must be a welcome relief..

---

### Post by gga96 on 2016-02-18
Thanks blm-ubunet for the info. RAIN, yes very welcome, the dams are a little fuller but the fires are still burning.

---

