---
title: "How to get patches in 0.25-fixes ?"
date: 2012-09-12
forum: Mythbuntu
---

### Post by Henk Poley on 2012-09-12
Would it be possible to get [https://github.com/MythTV/mythtv/pull/24](https://github.com/MythTV/mythtv/pull/24) into 0.25-fixes in Mythbuntu? Who should I contact?

---

### Post by tgm4883 on 2012-09-12
> **Henk Poley said:**
> Would it be possible to get [https://github.com/MythTV/mythtv/pull/24](https://github.com/MythTV/mythtv/pull/24) into 0.25-fixes in Mythbuntu? Who should I contact?

According to that link you posted, it's already in 0.25+fixes, so it should be available in the 0.25 updates repo.

---

### Post by Henk Poley on 2012-09-12
Doesn't "open" and "pull request" mean it's still under evaluation? And it says "Open bas-t **wants to** merge 1 commit". Also, the bug report ( [http://code.mythtv.org/trac/ticket/7486](http://code.mythtv.org/trac/ticket/7486) ) doesn't show any progress, in the sense that it has been committed. Or maybe I'm missing something.

---

### Post by tgm4883 on 2012-09-12
> **Henk Poley said:**
> Doesn't "open" and "pull request" mean it's still under evaluation? And it says "Open bas-t **wants to** merge 1 commit". Also, the bug report ( [http://code.mythtv.org/trac/ticket/7486](http://code.mythtv.org/trac/ticket/7486) ) doesn't show any progress, in the sense that it has been committed. Or maybe I'm missing something.

Sorry just skimmed it. You're right, it's not committed yet. It probably needs some testing, which means you'll need to follow [http://www.mythbuntu.org/wiki/recipes](http://www.mythbuntu.org/wiki/recipes) and apply the patch there. Looks like you'll probably also need to slightly modify the build script if you are building on 11.04 or newer. See [https://github.com/MythTV/packaging/pull/26](https://github.com/MythTV/packaging/pull/26)

---

### Post by Henk Poley on 2012-09-12
Except the packaging.git build script for debs errors out, since get-build-deps was removed in 12.04. Guess I'll just need to build a vanilla mythtv from source.

[https://github.com/MythTV/packaging/pull/26](https://github.com/MythTV/packaging/pull/26) <-- that one is closed but not merged..

I wonder how mythbuntu's buildbots churn out a release now.

---

### Post by tgm4883 on 2012-09-12
> **Henk Poley said:**
> Except the packaging.git build script for debs errors out, since get-build-deps was removed in 12.04. Guess I'll just need to build a vanilla mythtv from source.

[https://github.com/MythTV/packaging/pull/26](https://github.com/MythTV/packaging/pull/26) <-- that one is closed but not merged..

I wonder how mythbuntu's buildbots churn out a release now.

Which is why I said you would need to slightly modify it. (for instance, maybe comment the part where it grabs build deps and instead install build deps yourself? or look at [https://github.com/MythTV/packaging/pull/27](https://github.com/MythTV/packaging/pull/27) and see if that resolves it)

Mythbuntu builds are still done on 10.04, so they don't run into this issue.

---

