# Elevate-Labs-Task-4📑 Task 4 —  Report
Prepared by: Anuj Sawant (@MR_HACKER2611)
 Date: 26 September 2025

1. Objective
Is task ka objective firewall configuration aur network traffic filtering ka practical exposure lena tha. Humne Windows Firewall me rules banaye jisse ek insecure port (Telnet 23) ko block kiya aur secure port (SSH 22) ko allow kiya.

2. Tools Used
OS: Windows 10


Firewall: Windows Defender Firewall with Advanced Security


Verification Tool: PowerShell



3. Steps Performed
Step 1 — Open Firewall
Control Panel → Windows Defender Firewall → Advanced Settings open kiya.


(Screenshoot) <img width="1918" height="1060" alt="Screenshot 2025-09-26 082857" src="https://github.com/user-attachments/assets/a360d930-f6f5-47ab-b852-cde6aa1a5715" />

Step 2 — Block Telnet (Port 23)
Inbound Rules → New Rule → Port → TCP → Specific Port 23 → Block connection.


Rule created as Block Telnet Port 23.


(Screenshot: Block rule created)<img width="1919" height="1079" alt="Screenshot 2025-09-26 084054" src="https://github.com/user-attachments/assets/f141b529-f9ae-4cba-a2a2-7b8d5412aa89" />


Step 3 — Allow SSH (Port 22)
Inbound Rules → New Rule → Port → TCP → Specific Port 22 → Allow connection.


Rule created as Allow SSH Port 22.


(Screenshot: Allow rule created)<img width="1309" height="1002" alt="Screenshot 2025-09-26 085510" src="https://github.com/user-attachments/assets/6b5a1401-289d-4dd2-a50a-58a1380cfcee" />



Step 4 — Test Rules (PowerShell)
Commands executed:

 Test-NetConnection -Port 23 -ComputerName localhost
Test-NetConnection -Port 22 -ComputerName localhost


Result:


Port 23 → Blocked (TcpTestSucceeded : False) ✅


Port 22 → No service running (Windows me default SSH nahi hota, isliye False) ✅


(Screenshot: PowerShell results)<img width="1914" height="1025" alt="Screenshot 2025-09-26 084541" src="https://github.com/user-attachments/assets/0afb9b55-a118-4a7c-b609-a95ce01e2374" />


Step 5 — Remove Rule
Inbound Rules → Deleted Block Telnet (Port 23) rule.


Firewall restored to original state.


(Screenshot: Rule deleted)<img width="1919" height="1060" alt="Screenshot 2025-09-26 084816" src="https://github.com/user-attachments/assets/8688ea12-62d1-4e7a-a39b-acfcd1e1c671" />



4. Observations
Firewall rules successfully applied and tested.


Blocking insecure ports prevents potential attacks.


Even though Windows pe SSH service default off hoti hai, allow rule successfully created.



5. Conclusion
Firewall ek effective security layer hai jo unwanted traffic block karta hai aur sirf allowed services ko open rakhta hai. Is task ne mujhe firewall ka hands-on exposure diya jo real-world system hardening ke liye important hai.

6. Interview Q&A
Q1. What is a firewall?
 Firewall ek network security system hai jo incoming aur outgoing traffic ko rules ke basis pe allow/block karta hai.
Q2. Difference between Stateful and Stateless firewall?
Stateful → Connection states track karta hai (context aware).


Stateless → Sirf individual packets check karta hai (context unaware).


Q3. Inbound vs Outbound rules?
Inbound → External traffic jo system me aa raha hai.


Outbound → Internal traffic jo system se bahar ja raha hai.


Q4. UFW ka role kya hai Linux me?
 UFW (Uncomplicated Firewall) iptables ko simple command-line interface deta hai.
Q5. Port 23 (Telnet) block kyun karte hain?
 Telnet insecure hai (plain text transmission), isliye attackers easily sniff kar sakte hain.
Q6. Common firewall mistakes?
Unused ports ko open chhod dena.


“Allow All” rules lagana.


Rules ko properly document na karna.


Q7. Firewall network security kaise improve karta hai?
 Unauthorized traffic block karke aur sirf trusted communication allow karke.
Q8. NAT in firewall kya hai?
 Network Address Translation internal IPs ko hide karta hai aur ek public IP ke zariye multiple devices ko internet access deta hai.

