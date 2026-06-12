---
title: "Why isn't cinelerra in the repositories?"
date: 2010-11-11
forum: Multimedia Software
---

### Post by houseworkshy on 2010-11-11
I know that one can put cinelerra in easily enough, they have made it very easy

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

What I don't understand is why it isn't in the Ubuntu repositories, it has been around a quite a while, cinelerraCV seems to fit the FOSS guidelines ( or does it?) and ( I know that this is only my own bias ) it is far and away the best video editor I have seen for linux or otherwise and it's quite a small file.  I suppose it does crash a bit but opens again in an instant right back where one was.  Don't they want it in the Ubuntu repositories or doesn't Ubuntu think it's fit enough for some reason.  I don't much like having to add ppa's but usually end up adding akirid.
Is there something wrong with this program or license?  Just wondered.

---

### Post by SeijiSensei on 2010-11-11
[https://bugs.launchpad.net/ubuntu/+bug/267614](https://bugs.launchpad.net/ubuntu/+bug/267614)

I think there are issues regarding licensing, but I'm just speculating based on reading that bug report.

---

### Post by houseworkshy on 2010-11-11
Thanks that seems to be why

"On Saturday 01 October 2005 15:44, Sam Hocevar wrote:
 >    Be careful, more than 1000 Cinelerra source files do not have a
> proper license, a dozen are copyrighted by the MPEG group, another dozen
> are under the old ugly OpenDivX license, and you have many additional
> strange licensing terms in some files (such as free to copy and modify,
> but not to redistribute)."  

Which seems a good explaination.  Pity, maybe someday one could work out something similar to "restricted extras" or for programs like this, or perhaps it could go in mediabuntu ( which is another ppa of cource).  I suppose I simply have more faith in the packages which are maintained or at least checked by Ubuntu developers.  
I'll marked this solved in a day or two but leave it for now as the date of the quoted post is a few years old on the offchance someone may know of some recent change and would like to chime in.  Looks like a very active project still.

You found that quick, thanks.

---

### Post by cotcot on 2010-11-11
You can easily install the [[COLOR="Red"]akirad[/COLOR]]("https://launchpad.net/~akirad/+archive/akirad") repository. Then you can get cinelerra through synaptic just as the other packages.

---

### Post by feranick on 2010-12-04
Builds for Maverick, Lucid, Karmic and Hardy of the latest version of Cinelerra 2.1.5CV are available in this PPA:

[https://launchpad.net/~cinelerra-ppa](https://launchpad.net/~cinelerra-ppa)

---

