# Use the official Ruby image
FROM ruby:3.0

RUN ln -sf /bin/bash /bin/sh

# User
RUN useradd -m jekyll

# Install dependencies
RUN apt-get update && apt-get install -y curl && curl -sL https://deb.nodesource.com/setup_18.x | bash - && apt-get install -y nodejs && apt-get clean

# Ensure gem is up-to-date
RUN gem update --system

# Install Jekyll and Bundler
RUN gem install jekyll bundler

# Set the working directory
WORKDIR /workspace

# Copy the Gemfile and Gemfile.lock if they exist
COPY ../Gemfile ../Gemfile.lock* /workspace/

# Install the gems specified in the Gemfile
RUN bundle install

# Copy the rest of the application code
COPY .. .

# Expose the port Jekyll will run on
EXPOSE 4000

# Default command to run when starting the container
#CMD ["bundle", "exec", "jekyll", "serve", "--host", "0.0.0.0"]