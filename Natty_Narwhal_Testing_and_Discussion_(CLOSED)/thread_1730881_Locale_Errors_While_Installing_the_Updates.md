---
title: "Locale Errors While Installing the Updates"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by desaivarun_104lts on 2011-04-16
Hi,

Everytime i install the updates,i am getting these locale errors.How to avoid them..These are not causing any problems to updates,still i want to avoid these type of errors.

Suggest me what to do,so that i will not get these locale errors again and again.

---

### Post by Blasphemist on 2011-04-16
I'm not positive this will be the fix but it won't do any harm and may fix it. Open synaptic package manager and under the edit menu choose fix broken packages. Please do let me know if this works.

---

### Post by Harry33 on 2011-04-16
> **desaivarun_104lts said:**
> Hi,
Everytime i install the updates,i am getting these locale errors.How to avoid them..These are not causing any problems to updates,still i want to avoid these type of errors.
Suggest me what to do,so that i will not get these locale errors again and again.

What language packs do you have installed.
Check with Synaptic (for example language-pack-en, language-pack-en-base).

---

### Post by 5149.5 on 2011-04-16
Try:


```
sudo dpkg-reconfigure localeconf
```

---

### Post by sikander3786 on 2011-04-16
If none of the advices posted above helps you, we need you to run and post the complete outputs of these commands from Applications > Accessories > Terminal please.

```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```

---

### Post by desaivarun_104lts on 2011-04-16
> **Blasphemist said:**
> I'm not positive this will be the fix but it won't do any harm and may fix it. Open synaptic package manager and under the edit menu choose fix broken packages. Please do let me know if this works.

Selected the option,no change in the synaptic.

---

### Post by dino99 on 2011-04-17
then switch to the main server if not yet

---

### Post by Blasphemist on 2011-04-17
I don't quite no what to tell you. Dino's instruction isn't clear to me but I'm still somewhat a noob, for sure compared to many here. I do like what Dan (user 5149.5) posts because it at least looks like it is reconfiguring what locale you are set to and that seems to be in your errors. When did you notice this starting? Had there been any change you can think of relating to locale? If anyone knows where all the local settings are set, please jump in.

I love that this thread is so international. A question from India, help attempts from Colorado, Finland, California, Pakistan and more. I'm particularly pleased to see a Pakistani helping an Indian.:D

---

