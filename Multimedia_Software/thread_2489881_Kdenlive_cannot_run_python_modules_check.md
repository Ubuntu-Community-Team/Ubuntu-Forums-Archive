---
title: "Kdenlive cannot run python modules check"
date: 2023-08-13
forum: Multimedia Software
---

### Post by gdesilva on 2023-08-13
Hi,

I am trying to run kdenlive automatic subtitle generation using in Ubunut Mate 23.04.

Since under Ubuntu 23.04 it is no longer possible to run python scripts unless they are run under a virtual environment, I used pipx to install python apps and managed to install python vosk speech to text module which is required for automatic subtitle generation. However, in kdenlive appears to be unable to locate the vosk module and throws up an error saying that module needs to be installed. 

How do I get kdenlive to use pipx for checking, installing and updating python modules it has to use?

Thanks

NB : already tried to set up venv and run 'pip3 install vosk' but it cannot find the vosk module and hence the attempt to use pipx

---

