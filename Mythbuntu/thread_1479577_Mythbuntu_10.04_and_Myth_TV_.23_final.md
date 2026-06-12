---
title: "Mythbuntu 10.04 and Myth TV .23 final"
date: 2010-05-10
forum: Mythbuntu
---

### Post by DarkAmeba on 2010-05-10
Semi new myth tv user here. I am looking to put together a myth system for a family member which I will be building from scratch. Mythbuntu is ideal because it is easy, however the current Mythbuntu .iso has build 24104 included with it. This is a .23 release candidate rather than the final release. Yes, I am probably nit picking, but I would rather have the final release installed, especially when the system lives in a home where I cannot easily troubleshoot issues.

When a final myth release hits (it just did today!) is there typically a re spun iso of Mythbuntu made available which incorporates the final version?

I had a nasty experience with auto builds so I am hesitant to use that. I could just build from an Ubuntu base like I will for my home setup, but for my dad the simplicity of Mythbuntu would be preferred.

Thanks in advance for any insight!

---

### Post by tgm4883 on 2010-05-10
No, there will not be a respin of the ISO with 0.23 unless it gets into the repos (requires a SRU I believe). As the mythbuntu devs recommend running auto-builds, what was the issue you had?

---

### Post by DarkAmeba on 2010-05-10
> **tgm4883 said:**
> No, there will not be a respin of the ISO with 0.23 unless it gets into the repos (requires a SRU I believe). As the mythbuntu devs recommend running auto-builds, what was the issue you had?

I had issues with auto builds messing with app armor in my 9.10 with .22. Installing an update would cause my frontends to lose connection to the backend, even on the machine that was running the backend locally! Traced the issue down to app armor, then just re imaged the machine rather than troubleshoot. :confused:

Will auto builds update a mythbuntu install to the same state as a manual install of the .23 final release would produce? 

If so, there's really no reason I shouldn't give auto builds another shot.

---

### Post by tgm4883 on 2010-05-10
> **DarkAmeba said:**
> I had issues with auto builds messing with app armor in my 9.10 with .22. Installing an update would cause my frontends to lose connection to the backend, even on the machine that was running the backend locally! Traced the issue down to app armor, then just re imaged the machine rather than troubleshoot. :confused:

Will auto builds update a mythbuntu install to the same state as a manual install of the .23 final release would produce? 

If so, there's really no reason I shouldn't give auto builds another shot.

Thats a really weird issue. auto-builds is using the same process to build the mythtv packages as the ones that are in the archive (and the repos only contain mythtv packages. -testing has more but you don't have to enable that). And the mythbuntu-repos package isn't doing anything that messes with apparmor. All -repos does is add a repo and install a repo key.

---

### Post by ZedThou on 2010-05-10
> **DarkAmeba said:**
> I had issues with auto builds messing with app armor in my 9.10 with .22. Installing an update would cause my frontends to lose connection to the backend, even on the machine that was running the backend locally! Traced the issue down to app armor, then just re imaged the machine rather than troubleshoot. :confused:

Will auto builds update a mythbuntu install to the same state as a manual install of the .23 final release would produce? 

If so, there's really no reason I shouldn't give auto builds another shot.

Oh wow, that sounds awfully familiar. Something similar happened to me - [http://ubuntuforums.org/showthread.php?t=1413692](http://ubuntuforums.org/showthread.php?t=1413692) - and there was never really any resolution as to what exactly had caused the problem to arise, but it was fixed with a simple edit.

---

### Post by DarkAmeba on 2010-05-11
> **ZedThou said:**
> Oh wow, that sounds awfully familiar. Something similar happened to me - [http://ubuntuforums.org/showthread.php?t=1413692](http://ubuntuforums.org/showthread.php?t=1413692) - and there was never really any resolution as to what exactly had caused the problem to arise, but it was fixed with a simple edit.

I'm really glad I'm not the only one! No one really understood what was going on (myself included) or why app armor was affected. It's great to see a fix though! Hopefully it is an issue which won't show its head again anyhow since there new myth version running on 10.04.

---

