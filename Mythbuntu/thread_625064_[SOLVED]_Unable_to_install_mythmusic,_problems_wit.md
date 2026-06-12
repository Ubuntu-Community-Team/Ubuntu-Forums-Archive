---
title: "[SOLVED] Unable to install mythmusic, problems with libflac7 package"
date: 2007-11-27
forum: Mythbuntu
---

### Post by KvZ on 2007-11-27
Hi All,

I have a problem installing mythmusic. I've enabled the Automated Weekly MythTV 0.20-fixes Builds (UK mirror).

When I try to enable MythMusic in the **Mythbuntu Control Centre **I get the error *'Broken apt package cache'*. apt-get update and upgrade seem to go fine. when I try to install the mythmusic package I get the following error

```

$ sudo apt-get install mythmusic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mythmusic: Depends: libflac7 but it is not installable
E: Broken packages

```

Trying to install libflac7 results in the following error

```

$ sudo apt-get install libflac7
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libflac7 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libflac7 has no installation candidate

```

Seaching the gusty package directories results in no matches. It seems to be replaced by the libflac8 package?

Any idee how to resolve this?

Thanks
Kasrten

---

### Post by superm1 on 2007-11-27
You have the feisty repositories enabled.  There was a typo on the page that was corrected a day or two ago.  It now reflects the gutsy repositories.

---

### Post by KvZ on 2007-11-27
Thanks, that was it.

Karsten

---

