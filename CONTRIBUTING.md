# Contributing to Medical Device Management System

Thank you for your interest in contributing to our project! We welcome contributions from everyone who shares our vision of improving healthcare through technology.

## 🌟 Our Philosophy: "How Can We Make It Work"

Before contributing, please understand our core philosophy:

1. **Welcome Problems** - Problems are opportunities for improvement
2. **Pragmatic Advancement** - Find workable solutions within constraints
3. **System Thinking** - Build systems that prevent recurrence
4. **Continuous Learning** - Extract reusable patterns from experience

## 🚀 Getting Started

### Prerequisites
- Basic understanding of our [Architecture](docs/architecture.md)
- Familiarity with our [Code of Conduct](CODE_OF_CONDUCT.md)
- Read our [Development Philosophy](docs/how-it-works.md)

### First Time Contributors
1. Look for issues labeled `good-first-issue` or `help-wanted`
2. Comment on the issue to express your interest
3. Wait for maintainer assignment before starting work
4. Follow the contribution process below

## 📋 Contribution Process

### 1. Fork and Clone
```bash
# Fork the repository on GitHub
# Clone your fork locally
git clone https://github.com/YOUR-USERNAME/medical-device-management-system.git
cd medical-device-management-system

# Add upstream remote
git remote add upstream https://github.com/Medical-System-Lab/medical-device-management-system.git
```

### 2. Create a Branch
```bash
# Create a descriptive branch name
git checkout -b feature/your-feature-name
# or
git checkout -b fix/issue-number-description
```

### 3. Make Your Changes
- Follow our [Coding Standards](#coding-standards)
- Write tests for new functionality
- Update documentation as needed
- Keep commits focused and descriptive

### 4. Test Your Changes
```bash
# Run backend tests
cd backend
npm test

# Run frontend tests
cd ../frontend
npm test

# Run integration tests
cd ../tests
npm test
```

### 5. Commit Your Changes
```bash
# Use conventional commit messages
git commit -m "feat: add new device import feature"
# or
git commit -m "fix: resolve authentication token expiration issue"
```

### 6. Push and Create Pull Request
```bash
# Push to your fork
git push origin feature/your-feature-name

# Create Pull Request on GitHub
# Fill out the PR template completely
```

## 🎯 Pull Request Guidelines

### PR Template
All PRs must use our PR template which includes:
- Description of changes
- Related issue number
- Testing performed
- Screenshots (if UI changes)
- Checklist of requirements

### Code Review Process
1. **Automated Checks** - CI/CD pipeline runs automatically
2. **Maintainer Review** - At least one maintainer reviews
3. **Feedback Incorporation** - Address review comments
4. **Approval** - Requires at least one maintainer approval
5. **Merge** - Maintainer merges after approval

### PR Requirements
- ✅ All tests pass
- ✅ Code follows style guidelines
- ✅ Documentation updated
- ✅ No breaking changes without discussion
- ✅ Backward compatibility maintained

## 📝 Coding Standards

### General Guidelines
- Write clear, readable code
- Use meaningful variable and function names
- Comment complex logic
- Keep functions small and focused
- Follow DRY (Don't Repeat Yourself) principle

### Backend (Node.js/Express)
```javascript
// Good example
const createDevice = async (deviceData) => {
  try {
    const device = await Device.create(deviceData);
    await logActivity('device_created', device.id);
    return device;
  } catch (error) {
    throw new AppError('Failed to create device', 500);
  }
};

// Bad example
const cd = async (dd) => {
  const d = await D.create(dd);
  return d;
};
```

### Frontend (React)
```jsx
// Good example
const DeviceCard = ({ device, onEdit, onDelete }) => {
  const { name, type, status } = device;
  
  return (
    <Card title={name}>
      <p>Type: {type}</p>
      <p>Status: {status}</p>
      <Button onClick={() => onEdit(device)}>Edit</Button>
      <Button danger onClick={() => onDelete(device.id)}>Delete</Button>
    </Card>
  );
};

// Bad example
const DC = ({ d, oe, od }) => (
  <div>
    <h2>{d.n}</h2>
    <button onClick={() => oe(d)}>E</button>
    <button onClick={() => od(d.i)}>D</button>
  </div>
);
```

### Commit Message Convention
We use [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

Examples:
```
feat(auth): add password reset functionality
fix(api): resolve device search pagination issue
docs(readme): update installation instructions
```

## 🧪 Testing Standards

### Unit Tests
- Test individual functions and components
- Mock external dependencies
- Aim for > 90% code coverage
- Use descriptive test names

```javascript
// Good test example
describe('Device Service', () => {
  describe('createDevice', () => {
    it('should create a new device with valid data', async () => {
      const deviceData = { name: 'Test Device', type: 'diagnostic' };
      const result = await createDevice(deviceData);
      expect(result).toHaveProperty('id');
      expect(result.name).toBe(deviceData.name);
    });
    
    it('should throw error with invalid data', async () => {
      const deviceData = { name: '' };
      await expect(createDevice(deviceData)).rejects.toThrow();
    });
  });
});
```

### Integration Tests
- Test API endpoints
- Test database interactions
- Test component integrations
- Use test database

### E2E Tests
- Test complete user workflows
- Use Cypress or similar framework
- Test critical paths

## 📚 Documentation Standards

### Code Documentation
- Use JSDoc for functions and classes
- Document complex algorithms
- Explain business logic decisions
- Keep comments up to date

```javascript
/**
 * Creates a new medical device in the system
 * @param {Object} deviceData - Device information
 * @param {string} deviceData.name - Device name
 * @param {string} deviceData.type - Device type
 * @param {number} deviceData.quantity - Initial quantity
 * @returns {Promise<Device>} Created device object
 * @throws {AppError} If validation fails or database error
 */
async function createDevice(deviceData) {
  // Implementation
}
```

### Project Documentation
- Keep README up to date
- Document architecture decisions
- Provide setup and deployment guides
- Include troubleshooting guides

## 🐛 Reporting Issues

### Bug Reports
When reporting bugs, please include:
1. Clear description of the issue
2. Steps to reproduce
3. Expected vs actual behavior
4. Environment details
5. Screenshots or error logs

### Feature Requests
When requesting features, please:
1. Describe the problem you're solving
2. Explain your proposed solution
3. Provide use cases
4. Consider implementation complexity

### Security Issues
**DO NOT** report security issues in public issues. Please email security@medical-system.dev with details.

## 🏆 Recognition

We value all contributions! Contributors will be:
- Listed in our [CONTRIBUTORS.md](CONTRIBUTORS.md) file
- Recognized in release notes
- Eligible for contributor perks
- Considered for maintainer roles

## ❓ Getting Help

- Check our [FAQ](docs/faq.md)
- Join our [Discord](https://discord.gg/medical-system)
- Ask in [GitHub Discussions](https://github.com/Medical-System-Lab/medical-device-management-system/discussions)
- Email: contributors@medical-system.dev

## 📄 License

By contributing, you agree that your contributions will be licensed under the project's [MIT License](LICENSE).

---

Thank you for contributing to making healthcare better through technology! 🏥💻

**"How can we make it work together!"**