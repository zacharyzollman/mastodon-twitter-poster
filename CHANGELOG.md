[2019-02-26] - Fix an overseen issue with pleroma status id which is a string. `rails db:migrate` needed after upgrade.

[2019-02-21] - Add option to use twitter.activitypub.actor or similar to mention twitter people

[2019-02-02] - Add admin status to users table. Instructions on how to make a user an admin are available in the README file. `rails db:migrate` needed after upgrade.

[2019-01-31] - Fix issue with pleroma status id which is a string. `rails db:migrate` needed after upgrade.

[2019-01-09] - Update gems and node dependencies. `bundle install` and `yarn install --pure-lockfile` needed after upgrade.

[2018-12-11] - Added BLOCKED_DOMAINS variable, more information on README.

[2018-12-01] - Added bulma-rtl, `yarn install --pure-lockfile` and `rails assets:precompile` needed after upgrade.

[2018-11-23] - Removed daemons. Recommended services changed, take a look on new recommendation.

*Action is needed!* For this release, you need to upgrade the code, install the needed dependencies, restart the service and then run the following from a rails console session (can be accessed by using `RAILS_ENV=production bundle exec rails console` from your server) :

```
Sidekiq::DeadSet.new.each do |job|
  job.retry
end

Sidekiq::RetrySet.new.each do |job|
  job.retry;
end
```

This will cause the current jobs to be switched to the new worker mode.

[2018-11-14] - Remove statsd, create env variables to use to statsd if wanted, service examples updated