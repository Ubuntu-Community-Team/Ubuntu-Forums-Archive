---
title: "Msi Wind - Keeps asking for authentication"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Spanklord on 2009-08-01
-- intro
so i wasted all my day trying to get my msi wind wireless working by installing reinstalling , adding drivers , and reinstalling etc to find out i had to press fn+f11. so i thought yay there goes my wireless.... but it didnt. 


-- what does work
if i disable all security on my router it works just fine out of the box. 

-- problem
if i try and join my network with wpa2 enabled and i type in the password it just goes bussy for a while to ask me for the password again a little later. 

-- other stuf
i tryed wicd ( wiach i now prefer because of its elegance) and that will just say " autenticating" and stop after a little while. 

now my router(belkin F5D8232-4 v10009) allows for both a private wireless network and a guest one ( both still requiring passwords and both i cant join ) 

-- things im going to try
just thought up that i should go and disable the guest account but this wont really be a good sollution because all the other stuff in the house uses the guest account 

please help


Edit----
after spending ALOT of time on this i finaly found that my belkin router had the option for wpa-psk or wpa2-psk or those combined . it was enabled for both of them . after switching to just wpa2-psk i finaly had a succesfull connection. 


hope i helped somebody perserve his day by solving this problem now

---

### Post by Spanklord on 2009-08-01
resorting to bumping

(tried wep security but that didnt work either )

---

### Post by srmccoy on 2009-08-01
I am having the exact same issue. I'm using an MSI Wind with the same Belkin router. Exact same symptoms as well. It will ask for security key, then the icon will spin for about 2-3 minutes, then it will ask for a key again. This time there will already be text in the box, but when you uncheck the option to view the key it's random letters/numbers.

---

### Post by Spanklord on 2009-08-01
yup exacly the same here. tried about everything i could think of so really hoping somebody has a new idea for me

---

### Post by Spanklord on 2009-08-01
Found another forum thread with the same problem also unresolved so hoping my bump will inspire somebody to help me fix this

---

### Post by srmccoy on 2009-08-02
I too was using a Belkin router and having these issues. I'm back home now, and my Linksys router with WPA gave no issues. 

I've also had no issues with anything BUT Belkin routers and Ubuntu with my Wind, so that might be something.

---

