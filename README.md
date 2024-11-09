INSTRUCTIONS:

Step 1:
  configure the .env file following the .env.example, this is to be done in 2 stages,
  as the codes for the mobile app push notifications can only be set up once the server is up.

Step 2:
  Configure logrotate settings for vaultwarden logs

```
  (yourcurrentpath)/vaultwarden/vw-logs/*.log {
      # Rotate daily
      daily
      # Rotate when the size is bigger than 5MB
      size 5M
      # Compress old log files
      compress
      # Keep 4 rotations of log files before removing or mailing to the address specified in a mail directive
      rotate 4
      # Truncate the original log file in place after creating a copy
      copytruncate
      # Don't panic if not found
      missingok
      # Don't rotate log if file is empty
      notifempty
      # Add date instead of number to rotated log file
      dateext
      # Date format of dateext
      dateformat -%Y-%m-%d-%s
  }
```

  Do the same for the fail2ban logs located at (yourcurrentpath)/fail2ban/config/log/fail2ban/*.log
